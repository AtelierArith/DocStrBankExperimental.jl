```
aws_tls_ctx_options_init_default_server_from_system_path(options, allocator, cert_reg_path)
```

サーバーモードで使用するためのオプションを初期化します。cert*reg*pathは、システムにインストールされた証明書/秘密鍵ペアへのパスです。例: CurrentUser\MY\<thumprint>

注意: これはWindowsでのみ動作します。

### プロトタイプ

```c
int aws_tls_ctx_options_init_default_server_from_system_path( struct aws_tls_ctx_options *options, struct aws_allocator *allocator, const char *cert_reg_path);
```
