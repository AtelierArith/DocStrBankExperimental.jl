```
aws_channel_slot_insert_end(channel, to_add)
```

Inserts to 'to_add' the end of the channel. Note that the first call to [`aws_channel_slot_new`](@ref)() adds it to the channel implicitly.

### Prototype

```c
int aws_channel_slot_insert_end(struct aws_channel *channel, struct aws_channel_slot *to_add);
```
