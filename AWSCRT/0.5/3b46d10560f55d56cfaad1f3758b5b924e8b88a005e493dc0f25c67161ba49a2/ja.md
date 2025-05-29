```
on_connection_resumed(
    connection::MQTTConnection,
    return_code::aws_mqtt_connect_return_code,
    session_present::Bool,
)
```

MQTT接続が自動的に再開されるたびに呼び出されるコールバック。

引数:

  * `connection (MQTTConnection)`: 接続。
  * `return_code (aws_mqtt_connect_return_code)`: サーバーから受信した接続戻りコード。
  * `session_present (Bool)`: 既存のセッションを再開している場合は`true`。新しいセッションの場合は`false`。この値が`false`の場合、サーバーはすべての以前のサブスクリプションを忘れています。サブスクリプションは[`resubscribe_existing_topics`](@ref)を介して再確立できます。

!!! note
    すべてのコールバックは同時に実行されます。コールバックの実装はスレッドセーフである必要があります。並行性の制限はありません。

