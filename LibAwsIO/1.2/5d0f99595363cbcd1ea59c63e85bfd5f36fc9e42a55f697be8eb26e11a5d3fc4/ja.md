```
aws_tls_ctx_options_init_client_mtls_with_custom_key_operations(options, allocator, custom, cert_file_contents)
```

クライアントモードでの相互TLSに使用するオプションを初期化します。このとき、秘密鍵操作はカスタムコードによって処理されます。

注意: cert*file*contentsは、この関数が呼び出された後に新しいバッファにコピーされるため、この関数を呼び出した後はそのデータを保持する必要はありません。

# 引数

  * `options`: [`aws_tls_ctx_options`](@ref) を初期化します。
  * `allocator`: 使用するアロケータ。
  * `custom`: カスタム鍵操作のオプション。
  * `cert_file_contents`: 証明書ファイルの内容。

### プロトタイプ

```c
int aws_tls_ctx_options_init_client_mtls_with_custom_key_operations( struct aws_tls_ctx_options *options, struct aws_allocator *allocator, struct aws_custom_key_op_handler *custom, const struct aws_byte_cursor *cert_file_contents);
```
