```
aws_event_stream_rpc_client_connection_send_protocol_message(connection, message_args, flush_fn, user_data)
```

Sends a message on the connection. These must be connection level messages (not application messages).

flush_fn will be invoked when the message has been successfully writen to the wire or when it fails.

returns AWS_OP_SUCCESS if the message was successfully created and queued, and in that case flush_fn will always be invoked. Otherwise, flush_fn will not be invoked.

### Prototype

```c
int aws_event_stream_rpc_client_connection_send_protocol_message( struct aws_event_stream_rpc_client_connection *connection, const struct aws_event_stream_rpc_message_args *message_args, aws_event_stream_rpc_client_message_flush_fn *flush_fn, void *user_data);
```
