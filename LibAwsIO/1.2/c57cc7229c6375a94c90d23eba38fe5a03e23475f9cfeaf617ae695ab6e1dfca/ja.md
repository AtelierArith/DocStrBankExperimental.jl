```
aws_tls_ctx_options_init_client_mtls_with_pkcs11(options, allocator, pkcs11_options)
```

クライアントモードでの相互TLSに使用するオプションを初期化します。ここでは、PKCS#11ライブラリが秘密鍵へのアクセスを提供します。

注意: これはUnixデバイスでのみ動作します。

# 引数

  * `options`: [`aws_tls_ctx_options`](@ref) を初期化します。
  * `allocator`: 使用するアロケータ。
  * `pkcs11_options`: PKCS#11を使用するためのオプション（内容はコピーされます）

### プロトタイプ

```c
int aws_tls_ctx_options_init_client_mtls_with_pkcs11( struct aws_tls_ctx_options *options, struct aws_allocator *allocator, const struct aws_tls_ctx_pkcs11_options *pkcs11_options);
```
