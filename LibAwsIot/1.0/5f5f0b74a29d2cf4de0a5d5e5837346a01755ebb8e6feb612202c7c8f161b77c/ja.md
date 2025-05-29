ユーザーコールバックタイプは、レポートの送信に失敗したときに呼び出されます。

送信失敗には2つの可能性があります。1. MQTTクライアントがメッセージの公開に失敗し、エラーコードを返します。このシナリオでは、client*error*codeはAWS*ERROR*SUCCESS以外の値になります。rejected*message*payloadパラメータはNULLになります。2. 成功裏に公開された後、該当するMQTT拒否トピックでメッセージを受信します。このシナリオでは、client*error*codeはAWS*ERROR*SUCCESSになり、rejected*message*payloadには受信した拒否メッセージのペイロードが含まれます。

# 引数

  * `rejected_message_payload`:[in] 拒否トピックから受信したレスポンスペイロード
  * `userdata`:[in] コールバックユーザーデータ
