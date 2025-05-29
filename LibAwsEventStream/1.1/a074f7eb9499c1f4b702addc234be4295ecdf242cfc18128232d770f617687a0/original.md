```
aws_event_stream_rpc_server_connection_from_existing_channel(server, channel, connection_options)
```

Bypasses server, and creates a connection on an already existing channel. No connection lifetime callbacks will be invoked on the returned connection. Returns NULL if an error occurs. If and only if, you use this API, the returned connection is already ref counted and you must call [`aws_event_stream_rpc_server_connection_release`](@ref)() even if you did not explictly call [`aws_event_stream_rpc_server_connection_acquire`](@ref)()

### Prototype

```c
struct aws_event_stream_rpc_server_connection * aws_event_stream_rpc_server_connection_from_existing_channel( struct aws_event_stream_rpc_server_listener *server, struct aws_channel *channel, const struct aws_event_stream_rpc_connection_options *connection_options);
```
