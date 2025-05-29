```
aws_tls_ctx_options_init_default_server(options, allocator, cert, pkey)
```

サーバーモードで使用するためのオプションを初期化します。certとpkeyはコピーされます。certとpkeyはPKCS#7 PEMアーマードとして扱われます。

### プロトタイプ

```c
int aws_tls_ctx_options_init_default_server( struct aws_tls_ctx_options *options, struct aws_allocator *allocator, struct aws_byte_cursor *cert, struct aws_byte_cursor *pkey);
```
