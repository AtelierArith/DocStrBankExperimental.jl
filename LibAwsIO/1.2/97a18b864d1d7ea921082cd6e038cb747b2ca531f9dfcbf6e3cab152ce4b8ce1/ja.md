```
aws_tls_ctx_options_init_server_pkcs12_from_path(options, allocator, pkcs12_path, pkcs_password)
```

サーバーモードで使用するためのオプションを初期化します。pkcs12*pathは、pkcs#12ファイルを含むディスク上のファイルへのパスです。ファイルは内部バッファにロードされます。pkcs*pwdはpkcs#12ファイルに対応するパスワードであり、コピーされます。

注意：これはAppleデバイスでのみ動作します。

### プロトタイプ

```c
int aws_tls_ctx_options_init_server_pkcs12_from_path( struct aws_tls_ctx_options *options, struct aws_allocator *allocator, const char *pkcs12_path, struct aws_byte_cursor *pkcs_password);
```
