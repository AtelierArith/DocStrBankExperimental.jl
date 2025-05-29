```
aws_tls_key_operation_get_digest_algorithm(operation)
```

操作のダイジェストが署名されているアルゴリズムを返します。実装がダイジェストアルゴリズムをサポートしていない場合は、TLS接続が停止するのを防ぐために [`aws_tls_key_operation_complete_with_error`](@ref)() を使用してください。

### プロトタイプ

```c
enum aws_tls_hash_algorithm aws_tls_key_operation_get_digest_algorithm(const struct aws_tls_key_operation *operation);
```
