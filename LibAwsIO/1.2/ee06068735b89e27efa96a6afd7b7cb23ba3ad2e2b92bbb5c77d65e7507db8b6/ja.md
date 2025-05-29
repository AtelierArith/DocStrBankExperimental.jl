```
aws_tls_connection_options_set_server_name(conn_options, allocator, server_name)
```

SNI拡張（どこでもサポートされています）およびx.509検証に使用するサーバー名を設定します。これを設定しないと、x.509検証が失敗する可能性があります。

### プロトタイプ

```c
int aws_tls_connection_options_set_server_name( struct aws_tls_connection_options *conn_options, struct aws_allocator *allocator, const struct aws_byte_cursor *server_name);
```
