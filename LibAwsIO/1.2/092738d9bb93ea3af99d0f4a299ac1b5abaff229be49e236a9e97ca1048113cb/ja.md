```
aws_tls_key_operation_get_type(operation)
```

カスタムキー操作によって実行する必要がある操作のタイプを返します。実装が操作を実行できない場合は、TLS接続が停止するのを防ぐために [`aws_tls_key_operation_complete_with_error`](@ref)() を使用してください。

### プロトタイプ

```c
enum aws_tls_key_operation_type aws_tls_key_operation_get_type(const struct aws_tls_key_operation *operation);
```
