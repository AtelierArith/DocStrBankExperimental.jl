```
Will(
    topic::String,
    qos::aws_mqtt_qos,
    payload::String,
    retain::Bool,
)
```

ウィルメッセージは、クライアントが予期せず失われた場合にサーバーによって公開されます。

ウィルメッセージは、クライアントが接続するときにサーバーに保存されます。クライアント接続がサーバーにDISCONNECTパケットが受信されることなく失われた場合に公開されます。

[MQTT-3.1.2-8]

引数:

  * `topic (String)`: ウィルメッセージを公開するトピック。
  * `qos (aws_mqtt_qos)`: ウィルメッセージを公開する際に使用されるQoS。
  * `payload (String)`: ウィルメッセージの内容。
  * `retain (Bool)`: ウィルメッセージが公開されたときに保持されるかどうか。
