```
aws_tls_ctx_options_set_verify_peer(options, verify_peer)
```

x.509 バリデーションを有効または無効にします。テストのためだけに無効にしてください。サーバーモードで相互 TLS を有効にするには、verify_peer を true に設定します。

### プロトタイプ

```c
void aws_tls_ctx_options_set_verify_peer(struct aws_tls_ctx_options *options, bool verify_peer);
```
