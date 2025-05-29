```
aws_event_stream_rpc_client_continuation_activate(continuation, operation_name, message_args, flush_fn, user_data)
```

Actually sends the initial stream to the peer. Callbacks from [`aws_event_stream_rpc_client_connection_new_stream`](@ref)() will actually be invoked if this function returns AWS_OP_SUCCESS, otherwise, the stream has not been queued and no callbacks will be invoked.

operation_name is the name to identify which logical rpc call you want to kick off with the peer. It must be non-empty. flush_fn will be invoked once the message has either been written to the wire or it fails.

### Prototype

```c
int aws_event_stream_rpc_client_continuation_activate( struct aws_event_stream_rpc_client_continuation_token *continuation, struct aws_byte_cursor operation_name, const struct aws_event_stream_rpc_message_args *message_args, aws_event_stream_rpc_client_message_flush_fn *flush_fn, void *user_data);
```
