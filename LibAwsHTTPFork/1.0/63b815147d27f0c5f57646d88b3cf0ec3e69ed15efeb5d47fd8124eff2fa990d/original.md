```
aws_http_message_new_response(allocator)
```

Create a new HTTP/1.1 response message. The message is blank, all properties (status, headers, etc) must be set individually.

The caller has a hold on the object and must call [`aws_http_message_release`](@ref)() when they are done with it.

### Prototype

```c
struct aws_http_message *aws_http_message_new_response(struct aws_allocator *allocator);
```
