```
aws_channel_slot_replace(remove, new_slot)
```

Replaces remove with new_slot. Deallocates remove and its handler.

### Prototype

```c
int aws_channel_slot_replace(struct aws_channel_slot *remove, struct aws_channel_slot *new_slot);
```
