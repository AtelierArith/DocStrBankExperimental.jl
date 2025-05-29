```
publish(client::ShadowClient, topic::String, payload::String, qos::aws_mqtt_qos)
```

ペイロードを構成されたシャドウトピックの下のトピックに公開します。

引数:

  * `client (ShadowClient)`: 使用するシャドウクライアント。
  * `topic (String)`: シャドウトピックプレフィックスを含まないトピック名。例: `/get`。
  * `payload (String)`: メッセージの内容。
  * `qos (aws_mqtt_qos)`: サーバーがクライアントにメッセージを送信する際に使用する最大要求QoS。サーバーはSUBACKで低いQoSを付与することがあります（返されたタスクを参照）。

タスクとPUBLISHパケットのIDを返します。QoSはタスクが完了するタイミングを決定します:

  * QoS 0の場合、パケットが送信されるとすぐに完了します。
  * QoS 1の場合、PUBACKが受信されると完了します。
  * QoS 2の場合、PUBCOMPが受信されると完了します。

成功した場合、タスクには次のメンバーを持つ辞書が含まれます:

  * `:packet_id (Int)`: 完了したPUBLISHパケットのID。

失敗した場合、タスクは例外をスローします。

MQTT接続またはネットワーク接続がない場合、タスクは永遠に待機する可能性があります。

PUBLISHパケットを送信できなかった場合はスローします。
