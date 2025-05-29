```
aws_http_message_new_request(allocator)
```

Create a new HTTP/1.1 request message. The message is blank, all properties (method, path, etc) must be set individually. If HTTP/1.1 message used in HTTP/2 connection, the transformation will be automatically applied. A HTTP/2 message will created and sent based on the HTTP/1.1 message.

The caller has a hold on the object and must call [`aws_http_message_release`](@ref)() when they are done with it.

### Prototype

```c
struct aws_http_message *aws_http_message_new_request(struct aws_allocator *allocator);
```
