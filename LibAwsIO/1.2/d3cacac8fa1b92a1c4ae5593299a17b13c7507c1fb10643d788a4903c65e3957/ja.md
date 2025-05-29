```
aws_custom_key_op_handler_perform_operation(key_op_handler, operation)
```

on*key*operation vtable 関数を呼び出します。関数の詳細については [`aws_custom_key_op_handler_vtable`](@ref) を参照してください。

### プロトタイプ

```c
void aws_custom_key_op_handler_perform_operation( struct aws_custom_key_op_handler *key_op_handler, struct aws_tls_key_operation *operation);
```
