```
aws_channel_handler_process_read_message(handler, slot, message)
```

Calls process_read_message on handler's vtable

### Prototype

```c
int aws_channel_handler_process_read_message( struct aws_channel_handler *handler, struct aws_channel_slot *slot, struct aws_io_message *message);
```
