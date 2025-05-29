```
aws_channel_slot_downstream_read_window(slot)
```

Fetches the downstream read window. This gives you the information necessary to honor the read window. If you call send_message() and it exceeds this window, the message will be rejected.

### Prototype

```c
size_t aws_channel_slot_downstream_read_window(struct aws_channel_slot *slot);
```
