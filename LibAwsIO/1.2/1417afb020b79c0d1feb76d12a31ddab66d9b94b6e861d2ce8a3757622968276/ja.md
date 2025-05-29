```
aws_tls_ctx_options_set_secitem_options(tls_ctx_options, secitem_options)
```

提供されたSecItemオプションをiOS/tvOS KeyChainに追加される証明書と秘密鍵に適用します。

注意: 現在、SecItemを使用するiOSおよびtvOSでのみサポートされています。

# 引数

  * `options`: [`aws_tls_ctx_options`](@ref) を修正します。
  * `secitem_options`: SecItemsのオプション

### プロトタイプ

```c
int aws_tls_ctx_options_set_secitem_options( struct aws_tls_ctx_options *tls_ctx_options, const struct aws_secitem_options *secitem_options);
```
