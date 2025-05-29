```
on_message(
    topic::String,
    payload::String,
    dup::Bool,
    qos::aws_mqtt_qos,
    retain::Bool,
)
```

メッセージを受信したときに呼び出されるコールバック。

引数:

  * `topic (String)`: メッセージを受信するトピック。
  * `payload (String)`: メッセージのペイロード。
  * `dup (Bool)`: DUPフラグ。Trueの場合、これはメッセージを送信する以前の試みの再配信である可能性があります。
  * `qos (aws_mqtt_qos)`: サーバーがクライアントにメッセージを送信する際に使用する最大要求QoS。サーバーはSUBACKで低いQoSを許可する場合があります（返されたタスクを参照）。
  * `retain (Bool)`: リテインフラグ。`true`の場合、メッセージはクライアントによる新しいサブスクリプションの結果として送信されました。

`nothing`を返します。

!!! note
    すべてのコールバックは同時に実行されます。コールバックの実装はスレッドセーフである必要があります。並行性の制限はありません。

