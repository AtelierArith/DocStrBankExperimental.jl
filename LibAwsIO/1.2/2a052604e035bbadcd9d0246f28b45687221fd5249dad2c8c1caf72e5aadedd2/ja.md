```
aws_tls_ctx_options_init_client_mtls(options, allocator, cert, pkey)
```

クライアントモードでの相互TLSに使用するオプションを初期化します。certとpkeyはコピーされます。certとpkeyはPKCS#7 PEMアーマードとして扱われます。

### プロトタイプ

```c
int aws_tls_ctx_options_init_client_mtls( struct aws_tls_ctx_options *options, struct aws_allocator *allocator, const struct aws_byte_cursor *cert, const struct aws_byte_cursor *pkey);
```
