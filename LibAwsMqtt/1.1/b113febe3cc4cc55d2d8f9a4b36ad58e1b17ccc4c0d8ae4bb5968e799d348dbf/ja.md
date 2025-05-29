```
aws_mqtt_client_connection_set_connection_closed_handler(connection, on_closed, on_closed_ud)
```

ユーザーのリクエストによって接続が正常に閉じられたときに呼び出すコールバックを設定します。これは接続が中断されたり失われたりするのとは異なり、成功した閉鎖のみをカバーします。

# 引数

  * `connection`:[in] 接続オブジェクト
  * `on_closed`:[in] 接続が閉じられたときに呼び出す関数
  * `on_closed_ud`:[in] on_closedのユーザーデータ

### プロトタイプ

```c
int aws_mqtt_client_connection_set_connection_closed_handler( struct aws_mqtt_client_connection *connection, aws_mqtt_client_on_connection_closed_fn *on_closed, void *on_closed_ud);
```
