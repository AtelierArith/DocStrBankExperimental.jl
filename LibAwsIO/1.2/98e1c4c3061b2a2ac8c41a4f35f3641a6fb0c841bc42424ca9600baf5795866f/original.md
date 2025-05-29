```
aws_channel_handler_shutdown(handler, slot, dir, error_code, free_scarce_resources_immediately)
```

calls shutdown_direction on handler's vtable.

### Prototype

```c
int aws_channel_handler_shutdown( struct aws_channel_handler *handler, struct aws_channel_slot *slot, enum aws_channel_direction dir, int error_code, bool free_scarce_resources_immediately);
```
