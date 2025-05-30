```
aws_mqtt_client_connection_set_on_any_publish_handler(connection, on_any_publish, on_any_publish_ud)
```

ANYのパブリッシュパケットが受信されるたびに呼び出されるコールバックを設定します。接続されていないときにのみ設定するのが安全です。

# 引数

  * `connection`:[in] 接続オブジェクト
  * `on_any_publish`:[in] パブリッシュが受信されたときに呼び出される関数（NULLを渡すと解除されます）
  * `on_any_publish_ud`:[in] on*any*publishのユーザーデータ

### プロトタイプ

```c
int aws_mqtt_client_connection_set_on_any_publish_handler( struct aws_mqtt_client_connection *connection, aws_mqtt_client_publish_received_fn *on_any_publish, void *on_any_publish_ud);
```
