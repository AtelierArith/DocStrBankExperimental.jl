```
aws_tls_ctx_options_init_server_pkcs12(options, allocator, pkcs12, pkcs_password)
```

サーバーモードで使用するためのオプションを初期化します。pkcs12はpkcs#12証明書と秘密鍵を含むバッファであり、コピーされます。pkcs_pwdはpkcs#12バッファに対応するパスワードであり、コピーされます。

注意: これはAppleデバイスでのみ動作します。

### プロトタイプ

```c
int aws_tls_ctx_options_init_server_pkcs12( struct aws_tls_ctx_options *options, struct aws_allocator *allocator, struct aws_byte_cursor *pkcs12, struct aws_byte_cursor *pkcs_password);
```
