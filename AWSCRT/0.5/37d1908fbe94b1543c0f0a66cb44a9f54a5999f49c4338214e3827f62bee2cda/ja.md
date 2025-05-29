```
subscribe(client::ShadowClient, qos::aws_mqtt_qos, callback::OnShadowMessage)
```

指定されたシャドウドキュメントの下にあるすべてのトピックにワイルドカードを使用してサブスクライブします。これには以下が含まれますが、これに限定されません：

  * `/get/accepted`
  * `/get/rejected`
  * `/update/delta`
  * `/update/accepted`
  * `/update/documents`
  * `/update/rejected`
  * `/delete/accepted`
  * `/delete/rejected`

引数：

  * `client (ShadowClient)`: 使用するシャドウクライアント。
  * `qos (aws_mqtt_qos)`: サーバーがクライアントにメッセージを送信する際に使用する最大要求QoS。サーバーはSUBACKで低いQoSを付与することがあります（返されるタスクを参照）。
  * `callback (OnShadowMessage)`: メッセージを受信したときに呼び出されるコールバック。必要なシグネチャについては[`OnShadowMessage`](@ref)を参照してください。

各[`subscribe`](@ref)呼び出しからのタスクが完了すると完了するタスクを返します。また、各[`subscribe`](@ref)呼び出しからのパケットIDを含むコレクションも返します。
