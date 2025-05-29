```
aws_http_connection_make_request(client_connection, options)
```

Create a stream, with a client connection sending a request. The request does not start sending automatically once the stream is created. You must call [`aws_http_stream_activate`](@ref) to begin execution of the request.

The `options` are copied during this call.

Tip for language bindings: Do not bind the `options` struct. Use something more natural for your language, such as Builder Pattern in Java, or Python's ability to take many optional arguments by name.

Note: The header of the request will be sent as it is when the message to send protocol matches the protocol of the connection. - No `user-agent` will be added. - No security check will be enforced. eg: `referer` header privacy should be enforced by the user-agent who adds the header - When HTTP/1 message sent on HTTP/2 connection, [`aws_http2_message_new_from_http1`](@ref) will be applied under the hood. - When HTTP/2 message sent on HTTP/1 connection, no change will be made.

### Prototype

```c
struct aws_http_stream *aws_http_connection_make_request( struct aws_http_connection *client_connection, const struct aws_http_make_request_options *options);
```
