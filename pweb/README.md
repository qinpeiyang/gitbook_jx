# 个人网上银行

个人网上银行是指银行通过[互联网](https://baike.baidu.com/item/%E4%BA%92%E8%81%94%E7%BD%91/199186)，为个人客户提供账户查询、转账[汇款](https://baike.baidu.com/item/%E6%B1%87%E6%AC%BE/10098321)、投资理财、在线支付等金融服务的网上银行服务。使客户可以足不出户就能够安全便捷地管理活期和定期存款、支票、信用卡及个人投资等。个人网上银行客户分为注册客户和非注册客户两大类。注册客户按照注册方式分为柜面注册客户和自助注册客户，按是否申令证书分为证书客户和无证书客户。可以说，个人网上银行是在Internet上的虚拟银行柜台。



| name | value1 | value2 | value3 | value4 |
| :--: | :----: | :----: | :----: | :----: |
|  a   |   1    |   2    |   3    |   4    |
|  b   |   2    |   3    |   4    |   5    |
|  c   |   3    |   4    |   5    |   6    |
|  d   |   4    |   5    |   6    |   7    |
|  e   |   5    |   6    |   7    |   8    |



```java
if(hostReturnCodeValidatorFlag != null && hostReturnCodeValidatorFlag.equals("success")){
			//如果交易成功，则判断是否短信通知，先通过rule判断，再通过isMessageNotify。isMessageNotify如果是0，则表示短信通知，如果是1，则表示不短信通知
			//String isMessageNotify = (String)context.getData("MessageNotify");
			BankSysRule messageNotifyRule = cachedBankRuleAttribute.getResourceWithNull(bankSeq, CONSMSG.RULETYPE_FIELDFILTER, "PMessageNotify.MessageNotify");
			//如果短信通知
			if(messageNotifyRule != null && messageNotifyRule.getRuleDef().equals("Y") && isMessageNotify != null && isMessageNotify.equals("0")){
				try {
					this.issueHostTrs(context, tempMap);
				} catch (PeException e) {
					e.printStackTrace();
				}
			}
		}else{
			//如果交易失败，则判断失败后是否短信通知，先通过rule判断，再通过isMessageNotify。
			//String isMessageNotify = (String)context.getData("MessageNotify");
			BankSysRule messageNotifyFailRule = cachedBankRuleAttribute.getResourceWithNull(bankSeq, CONSMSG.RULETYPE_FIELDFILTER, "PMessageNotifyFail.MessageNotify");
			//如果失败后短信通知
			if(messageNotifyFailRule != null && messageNotifyFailRule.getRuleDef().equals("Y") && isMessageNotify != null && isMessageNotify.equals("0")){
				try {
					this.issueHostTrs(context, tempMap);
				} catch (PeException e) {
					e.printStackTrace();
				}
			}
		}
```

