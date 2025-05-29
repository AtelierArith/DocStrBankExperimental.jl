```
aws_event_stream_rpc_server_continuation_send_message(continuation, message_args, flush_fn, user_data)
```

Sends an application message on the continuation. If the message is valid and successfully written to the channel, flush_fn will be invoked.

### Prototype

```c
int aws_event_stream_rpc_server_continuation_send_message( struct aws_event_stream_rpc_server_continuation_token *continuation, const struct aws_event_stream_rpc_message_args *message_args, aws_event_stream_rpc_server_message_flush_fn *flush_fn, void *user_data);
```
