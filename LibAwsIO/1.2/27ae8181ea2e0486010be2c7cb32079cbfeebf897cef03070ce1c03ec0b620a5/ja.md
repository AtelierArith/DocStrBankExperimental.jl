```
aws_tls_key_operation_get_signature_algorithm(operation)
```

操作が期待されるアルゴリズムを返します。実装が署名アルゴリズムをサポートしていない場合は、TLS接続が停止するのを防ぐために [`aws_tls_key_operation_complete_with_error`](@ref)() を使用してください。

### プロトタイプ

```c
enum aws_tls_signature_algorithm aws_tls_key_operation_get_signature_algorithm( const struct aws_tls_key_operation *operation);
```
