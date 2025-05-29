```
aws_event_stream_channel_handler_write_message(handler, message, on_message_written, user_data)
```

Writes an [`aws_event_stream_message`](@ref)() to the channel. Once the channel flushes or an error occurs, on_message_written will be invoked. message should stay valid until the callback is invoked. If an error an occurs, the channel will automatically be shutdown.

### Prototype

```c
int aws_event_stream_channel_handler_write_message( struct aws_channel_handler *handler, struct aws_event_stream_message *message, aws_event_stream_channel_handler_on_message_written_fn *on_message_written, void *user_data);
```
