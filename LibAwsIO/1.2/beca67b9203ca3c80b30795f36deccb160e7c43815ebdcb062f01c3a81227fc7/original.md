```
aws_channel_slot_upstream_message_overhead(slot)
```

Fetches the current overhead of upstream handlers. This provides a hint to avoid fragmentation if you care.

### Prototype

```c
size_t aws_channel_slot_upstream_message_overhead(struct aws_channel_slot *slot);
```
