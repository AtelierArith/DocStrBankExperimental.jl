```
aws_tls_ctx_options_set_keychain_path(options, keychain_path_cursor)
```

!!! compat "非推奨"



クライアントモードで相互TLSを使用するために、証明書と秘密鍵を保存するカスタムキーチェーンパスを設定します。

注意: これはMacOSでのみ動作します。

### プロトタイプ

```c
int aws_tls_ctx_options_set_keychain_path( struct aws_tls_ctx_options *options, struct aws_byte_cursor *keychain_path_cursor);
```
