```
subscribe(protocol::MQTTProtocol, topic::String; qos::Int=1)
```

`protocol`のMQTTクライアントを指定された`qos`設定で`topic`に購読します。

# 戻り値

MosquittoエラーコードとメッセージID。
