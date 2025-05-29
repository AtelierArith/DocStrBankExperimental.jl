```
aws_tls_ctx_options_init_client_mtls_pkcs12_from_path(options, allocator, pkcs12_path, pkcs_pwd)
```

クライアントモードでの相互TLSに使用するオプションを初期化します。pkcs12*pathは、ディスク上のpkcs#12ファイルを含むファイルへのパスです。このファイルは内部バッファにロードされます。pkcs*pwdはpkcs#12ファイルに対応するパスワードであり、コピーされます。

注意: これはAppleデバイスでのみ動作します。

### プロトタイプ

```c
int aws_tls_ctx_options_init_client_mtls_pkcs12_from_path( struct aws_tls_ctx_options *options, struct aws_allocator *allocator, const char *pkcs12_path, const struct aws_byte_cursor *pkcs_pwd);
```
