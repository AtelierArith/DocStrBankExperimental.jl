```
aws_tls_key_operation_complete(operation, output)
```

成功したTLSプライベートキー操作を、その出力を提供することで完了します。出力はTLS接続にコピーされます。この呼び出しによって操作は解放されます。

この関数または[`aws_tls_key_operation_complete_with_error`](@ref)()を必ず呼び出す必要があります。これを行わないと、TLS接続が無期限に停止し、メモリがリークします。

### プロトタイプ

```c
void aws_tls_key_operation_complete(struct aws_tls_key_operation *operation, struct aws_byte_cursor output);
```
