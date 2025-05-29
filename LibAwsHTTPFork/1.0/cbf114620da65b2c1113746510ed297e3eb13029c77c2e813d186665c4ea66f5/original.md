```
aws_http2_message_new_response(allocator)
```

Create a new HTTP/2 response message. pseudo headers need to be set from [`aws_http2_headers_set_response_status`](@ref) to the headers of the [`aws_http_message`](@ref). Will be errored out if used in HTTP/1.1 connection.

The caller has a hold on the object and must call [`aws_http_message_release`](@ref)() when they are done with it.

### Prototype

```c
struct aws_http_message *aws_http2_message_new_response(struct aws_allocator *allocator);
```
