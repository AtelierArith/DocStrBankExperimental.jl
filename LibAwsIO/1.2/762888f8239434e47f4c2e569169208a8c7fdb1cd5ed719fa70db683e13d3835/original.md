```
aws_channel_slot_shutdown(slot, dir, err_code, free_scarce_resources_immediately)
```

Initiates shutdown on slot. callbacks->on_shutdown_completed will be called once the shutdown process is completed.

### Prototype

```c
int aws_channel_slot_shutdown( struct aws_channel_slot *slot, enum aws_channel_direction dir, int err_code, bool free_scarce_resources_immediately);
```
