```
aws_http_connection_get_remote_endpoint(connection)
```

HTTP接続のリモートエンドポイントを返します。

### プロトタイプ

```c
const struct aws_socket_endpoint *aws_http_connection_get_remote_endpoint(const struct aws_http_connection *connection);
```
