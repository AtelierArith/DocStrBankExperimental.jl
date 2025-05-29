```
aws_event_stream_rpc_client_connection_new_stream(connection, continuation_options)
```

Create a new stream. continuation_option's callbacks will not be invoked, and nothing will be sent across the wire until [`aws_event_stream_rpc_client_continuation_activate`](@ref)() is invoked.

returns an instance of a [`aws_event_stream_rpc_client_continuation_token`](@ref) on success with a reference count of 1. You must call [`aws_event_stream_rpc_client_continuation_release`](@ref)() when you're finished with it. Returns NULL on failure.

### Prototype

```c
struct aws_event_stream_rpc_client_continuation_token * aws_event_stream_rpc_client_connection_new_stream( struct aws_event_stream_rpc_client_connection *connection, const struct aws_event_stream_rpc_client_stream_continuation_options *continuation_options);
```
