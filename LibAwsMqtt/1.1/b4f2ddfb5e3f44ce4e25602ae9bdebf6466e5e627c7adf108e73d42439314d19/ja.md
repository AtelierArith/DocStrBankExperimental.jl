```
aws_mqtt_client_connection_set_connection_termination_handler(connection, on_termination, on_termination_ud)
```

接続の破棄時に呼び出すコールバックを設定します。

# 引数

  * `connection`:[in] 接続オブジェクト。
  * `on_termination`:[in] 接続が破棄されるときに呼び出される関数。
  * `on_termination_ud`:[in] on_termination のユーザーデータ。

### プロトタイプ

```c
int aws_mqtt_client_connection_set_connection_termination_handler( struct aws_mqtt_client_connection *connection, aws_mqtt_client_on_connection_termination_fn *on_termination, void *on_termination_ud);
```
