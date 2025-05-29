```
aws_tls_key_operation_complete_with_error(operation, error_code)
```

失敗したTLSプライベートキー操作を完了します。TLS接続は失敗します。この呼び出しによって操作は解放されます。

この関数または[`aws_tls_key_operation_complete`](@ref)()を必ず呼び出す必要があります。これを行わないと、TLS接続が無期限に停止し、メモリがリークします。

### プロトタイプ

```c
void aws_tls_key_operation_complete_with_error(struct aws_tls_key_operation *operation, int error_code);
```
