```
aws_channel_slot_insert_left(slot, to_add)
```

inserts 'to_add' to the position immediately to the left of slot. Note that the first call to [`aws_channel_slot_new`](@ref)() adds it to the channel implicitly.

### Prototype

```c
int aws_channel_slot_insert_left(struct aws_channel_slot *slot, struct aws_channel_slot *to_add);
```
