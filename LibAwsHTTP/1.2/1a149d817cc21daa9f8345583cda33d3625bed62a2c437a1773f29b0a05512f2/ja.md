```
aws_http_connection_configure_server(connection, options)
```

サーバー接続を構成します。これは、サーバーの on*incoming*connection コールバックから呼び出す必要があります。

### プロトタイプ

```c
int aws_http_connection_configure_server( struct aws_http_connection *connection, const struct aws_http_server_connection_options *options);
```
