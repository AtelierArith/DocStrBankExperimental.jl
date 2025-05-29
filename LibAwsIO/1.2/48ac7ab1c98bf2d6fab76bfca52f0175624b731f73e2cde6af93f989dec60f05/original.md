```
aws_channel_handler_increment_read_window(handler, slot, size)
```

Calls on_window_update on handler's vtable.

### Prototype

```c
int aws_channel_handler_increment_read_window( struct aws_channel_handler *handler, struct aws_channel_slot *slot, size_t size);
```
