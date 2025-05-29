```
on_shadow_message(
    shadow_client::ShadowClient,
    topic::String,
    payload::String,
    dup::Bool,
    qos::aws_mqtt_qos,
    retain::Bool,
)
```

受信したシャドウドキュメントメッセージに対して呼び出されるコールバック。

引数:

  * `shadow_client (ShadowClient)`: メッセージを受信したシャドウクライアント。
  * `topic (String)`: メッセージを受信するトピック。
  * `payload (String)`: メッセージのペイロード。
  * `dup (Bool)`: DUPフラグ。`true`の場合、これはメッセージを送信する以前の試みの再配信である可能性があります。
  * `qos (aws_mqtt_qos)`: サーバーがクライアントにメッセージを送信する際に使用する最大要求QoS。サーバーはSUBACKで低いQoSを付与することがあります（返されたタスクを参照）。
  * `retain (Bool)`: リテインフラグ。`true`の場合、メッセージはクライアントによる新しいサブスクリプションの結果として送信されました。

`nothing`を返します。
