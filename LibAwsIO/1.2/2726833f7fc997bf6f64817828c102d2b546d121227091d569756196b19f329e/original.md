```
aws_channel_slot_increment_read_window(slot, window)
```

Issues a window update notification upstream (to the left.)

### Prototype

```c
int aws_channel_slot_increment_read_window(struct aws_channel_slot *slot, size_t window);
```
