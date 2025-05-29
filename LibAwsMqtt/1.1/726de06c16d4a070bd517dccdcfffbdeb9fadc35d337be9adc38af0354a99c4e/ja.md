```
aws_mqtt_client_connection_set_login(connection, username, password)
```

CONNECTパケットと共に送信するユーザー名および/またはパスワードを設定します。

# 引数

  * `connection`:[in] 接続オブジェクト
  * `username`:[in] 接続するためのユーザー名
  * `password`:[in] [オプション] 接続するためのパスワード

### プロトタイプ

```c
int aws_mqtt_client_connection_set_login( struct aws_mqtt_client_connection *connection, const struct aws_byte_cursor *username, const struct aws_byte_cursor *password);
```
