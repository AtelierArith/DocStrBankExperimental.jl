```
aws_tls_connection_options_set_alpn_list(conn_options, allocator, alpn_list)
```

ALPNリストを<protocol1;protocol2;...>の形式で設定します。最大4つのプロトコルがサポートされています。alpn*listはコピーされます。この値はすでに[`aws*tls*ctx`](@ref)から継承されていますが、[`aws*tls_ctx`](@ref)はコストが高いため、できるだけ多くの接続で使用するべきです。この接続ごとに設定したい場合は、ここで設定してください。

### プロトタイプ

```c
int aws_tls_connection_options_set_alpn_list( struct aws_tls_connection_options *conn_options, struct aws_allocator *allocator, const char *alpn_list);
```
