```
aws_event_stream_rpc_client_continuation_send_message(continuation, message_args, flush_fn, user_data)
```

Sends a message on the continuation. [`aws_event_stream_rpc_client_continuation_activate`](@ref)() must be successfully invoked prior to calling this function.

If this function returns AWS_OP_SUCCESS, flush_fn will be invoked once the message has either been written to the wire or it fails.

### Prototype

```c
int aws_event_stream_rpc_client_continuation_send_message( struct aws_event_stream_rpc_client_continuation_token *continuation, const struct aws_event_stream_rpc_message_args *message_args, aws_event_stream_rpc_client_message_flush_fn *flush_fn, void *user_data);
```
