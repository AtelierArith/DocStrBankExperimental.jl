```
aws_channel_slot_on_handler_shutdown_complete(slot, dir, err_code, free_scarce_resources_immediately)
```

Called by handlers once they have finished their shutdown in the 'dir' direction. Propagates the shutdown process to the next handler in the channel.

### Prototype

```c
int aws_channel_slot_on_handler_shutdown_complete( struct aws_channel_slot *slot, enum aws_channel_direction dir, int err_code, bool free_scarce_resources_immediately);
```
