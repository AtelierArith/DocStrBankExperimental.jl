```
aws_event_stream_rpc_server_connection_send_protocol_message(connection, message_args, flush_fn, user_data)
```

Sends a protocol message on the connection (not application data). If the message is valid and successfully written to the channel, flush_fn will be invoked.

### Prototype

```c
int aws_event_stream_rpc_server_connection_send_protocol_message( struct aws_event_stream_rpc_server_connection *connection, const struct aws_event_stream_rpc_message_args *message_args, aws_event_stream_rpc_server_message_flush_fn *flush_fn, void *user_data);
```
