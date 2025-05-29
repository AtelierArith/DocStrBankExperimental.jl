```
aws_tls_connection_options_init_from_ctx(conn_options, ctx)
```

[`aws_tls_ctx`](@ref) のインスタンスからデフォルトの接続オプションを初期化します。

### プロトタイプ

```c
void aws_tls_connection_options_init_from_ctx( struct aws_tls_connection_options *conn_options, struct aws_tls_ctx *ctx);
```
