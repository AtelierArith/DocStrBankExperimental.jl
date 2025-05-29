```
aws_tls_ctx_options_init_client_mtls_from_path(options, allocator, cert_path, pkey_path)
```

クライアントモードでの相互TLSに使用するオプションを初期化します。cert*pathとpkey*pathはディスク上のファイルへのパスです。cert*pathとpkey*pathはPKCS#7 PEMアーマードとして扱われます。これらはディスクから読み込まれ、内部的にバッファに格納されます。

### プロトタイプ

```c
int aws_tls_ctx_options_init_client_mtls_from_path( struct aws_tls_ctx_options *options, struct aws_allocator *allocator, const char *cert_path, const char *pkey_path);
```
