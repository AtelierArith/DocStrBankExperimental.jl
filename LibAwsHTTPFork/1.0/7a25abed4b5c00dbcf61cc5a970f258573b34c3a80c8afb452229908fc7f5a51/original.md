```
aws_http_stream_activate(stream)
```

Only used for client initiated streams (immediately following a call to [`aws_http_connection_make_request`](@ref)).

Activates the request's outgoing stream processing.

### Prototype

```c
int aws_http_stream_activate(struct aws_http_stream *stream);
```
