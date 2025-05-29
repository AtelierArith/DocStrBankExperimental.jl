```
aws_tls_ctx_options_set_extension_data(options, extension_data)
```

BYO*CRYPTOを実装する際に、TLS実装に渡す追加データが必要な場合は、ここで設定します。extension*dataのライフタイムはoptionsオブジェクトよりも長くなければならず、optionsがクリーンアップされた後にクリーンアップされる必要があります。

### プロトタイプ

```c
void aws_tls_ctx_options_set_extension_data(struct aws_tls_ctx_options *options, void *extension_data);
```
