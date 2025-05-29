```
aws_http_message_new_request_with_headers(allocator, existing_headers)
```

Like [`aws_http_message_new_request`](@ref)(), but uses existing [`aws_http_headers`](@ref) instead of creating a new one. Acquires a hold on the headers, and releases it when the request is destroyed.

### Prototype

```c
struct aws_http_message *aws_http_message_new_request_with_headers( struct aws_allocator *allocator, struct aws_http_headers *existing_headers);
```
