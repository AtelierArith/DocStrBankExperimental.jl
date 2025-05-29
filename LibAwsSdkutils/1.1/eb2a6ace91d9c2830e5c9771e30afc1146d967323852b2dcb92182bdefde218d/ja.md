```
aws_endpoints_request_context_add_string_array(allocator, context, name, value_array, len)
```

ドキュメントが見つかりません。

### プロトタイプ

```c
int aws_endpoints_request_context_add_string_array( struct aws_allocator *allocator, struct aws_endpoints_request_context *context, struct aws_byte_cursor name, const struct aws_byte_cursor *value_array, size_t len);
```
