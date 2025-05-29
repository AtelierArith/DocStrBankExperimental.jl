```
aws_http_stream_new_server_request_handler(options)
```

Create a stream, with a server connection receiving and responding to a request. This function can only be called from the [`aws_http_on_incoming_request_fn`](@ref) callback. [`aws_http_stream_send_response`](@ref)() should be used to send a response.

### Prototype

```c
struct aws_http_stream *aws_http_stream_new_server_request_handler( const struct aws_http_request_handler_options *options);
```
