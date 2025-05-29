```
subscribe(client::ShadowClient, topic::String, qos::aws_mqtt_qos, callback::OnMessage)
```

指定されたシャドウドキュメントの下で、与えられた `topic`（先頭にスラッシュ（`/`）を含む必要があります）にサブスクライブします。

引数:

  * `client (ShadowClient)`: 使用するシャドウクライアント。
  * `topic (String)`: 与えられたシャドウドキュメントの下で、ワイルドカードを含む可能性のあるこのトピックフィルターにサブスクライブします。
  * `qos (aws_mqtt_qos)`: サーバーがクライアントにメッセージを送信する際に使用する最大要求QoS。サーバーはSUBACKで低いQoSを付与する場合があります（返されたタスクを参照）。
  * `callback (OnMessage)`: メッセージを受信したときに呼び出されるコールバック。必要なシグネチャについては[`OnMessage`](@ref)を参照してください。

タスクとSUBSCRIBEパケットのIDを返します。タスクはサーバーからSUBACKを受信すると完了します。

成功した場合、タスクは以下のメンバーを持つ辞書を含みます:

  * `:packet_id (Int)`: 確認されているSUBSCRIBEパケットのID。
  * `:topic (String)`: 確認されているSUBSCRIBEパケットのトピックフィルター。
  * `:qos (aws_mqtt_qos)`: サーバーによって付与された最大QoS。これは要求されたQoSよりも低い場合があります。

失敗した場合、タスクは例外を含みます。

MQTT接続またはネットワーク接続がない場合、タスクは永遠に待機する可能性があります。

SUBSCRIBEパケットを送信できなかった場合は例外をスローします。
