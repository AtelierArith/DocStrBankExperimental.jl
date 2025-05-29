```
aws_mqtt_client_connection_set_connection_interruption_handlers(connection, on_interrupted, on_interrupted_ud, on_resumed, on_resumed_ud)
```

接続が中断され、再開されたときに呼び出すコールバックを設定します。

# 引数

  * `connection`:[in] 接続オブジェクト
  * `on_interrupted`:[in] 接続が失われたときに呼び出す関数
  * `on_interrupted_ud`:[in] on_interrupted のユーザーデータ
  * `on_resumed`:[in] 接続が再開されたときに呼び出す関数（clean*session が true の場合、[`aws*mqtt*resubscribe*existing_topics`](@ref) を呼び出すことを推奨します）
  * `on_resumed_ud`:[in] on_resumed のユーザーデータ

### プロトタイプ

```c
int aws_mqtt_client_connection_set_connection_interruption_handlers( struct aws_mqtt_client_connection *connection, aws_mqtt_client_on_connection_interrupted_fn *on_interrupted, void *on_interrupted_ud, aws_mqtt_client_on_connection_resumed_fn *on_resumed, void *on_resumed_ud);
```
