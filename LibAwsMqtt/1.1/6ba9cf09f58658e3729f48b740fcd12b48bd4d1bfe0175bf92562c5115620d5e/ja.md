```
aws_mqtt_client_connection_set_connection_result_handlers(connection, on_connection_success, on_connection_success_ud, on_connection_failure, on_connection_failure_ud)
```

接続が成功または失敗したときに呼び出すコールバックを設定します

# 引数

  * `connection`:[in] 接続オブジェクト
  * `on_connection_success`:[in] 接続が成功したときまたは再開されたときに呼び出す関数
  * `on_connection_success_ud`:[in] on*connection*success のユーザーデータ
  * `on_connection_failure`:[in] 接続が失敗したときに呼び出す関数
  * `on_connection_failure_ud`:[in] on*connection*failure のユーザーデータ

### プロトタイプ

```c
int aws_mqtt_client_connection_set_connection_result_handlers( struct aws_mqtt_client_connection *connection, aws_mqtt_client_on_connection_success_fn *on_connection_success, void *on_connection_success_ud, aws_mqtt_client_on_connection_failure_fn *on_connection_failure, void *on_connection_failure_ud);
```
