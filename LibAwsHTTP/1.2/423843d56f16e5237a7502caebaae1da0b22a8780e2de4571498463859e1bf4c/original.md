```
aws_http2_message_new_from_http1(alloc, http1_msg)
```

Create an HTTP/2 message from HTTP/1.1 message. pseudo headers will be created from the context and added to the headers of new message. Normal headers will be copied to the headers of new message. Note: - if `host` exist, it will be removed and `:authority` will be added using the information. - `:scheme` always defaults to "https". To use a different scheme create the HTTP/2 message directly

### Prototype

```c
struct aws_http_message *aws_http2_message_new_from_http1( struct aws_allocator *alloc, const struct aws_http_message *http1_msg);
```
