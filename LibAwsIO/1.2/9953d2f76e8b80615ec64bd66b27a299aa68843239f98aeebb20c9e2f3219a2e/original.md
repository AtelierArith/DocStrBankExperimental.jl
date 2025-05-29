```
aws_channel_slot_set_handler(slot, handler)
```

Sets the handler for a slot, the slot will also call get_current_window_size() and propagate a window update upstream.

### Prototype

```c
int aws_channel_slot_set_handler(struct aws_channel_slot *slot, struct aws_channel_handler *handler);
```
