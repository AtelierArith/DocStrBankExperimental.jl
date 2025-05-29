```
aws_channel_slot_insert_right(slot, to_add)
```

inserts 'to_add' to the position immediately to the right of slot. Note that the first call to [`aws_channel_slot_new`](@ref)() adds it to the channel implicitly.

### Prototype

```c
int aws_channel_slot_insert_right(struct aws_channel_slot *slot, struct aws_channel_slot *to_add);
```
