```
aws_http_message_new_request_with_headers(allocator, existing_headers)
```

[`aws_http_message_new_request`](@ref)()と同様ですが、新しいものを作成する代わりに既存の[`aws_http_headers`](@ref)を使用します。ヘッダーを保持し、リクエストが破棄されるときに解放します。

### プロトタイプ

```c
struct aws_http_message *aws_http_message_new_request_with_headers( struct aws_allocator *allocator, struct aws_http_headers *existing_headers);
```
