```
aws_channel_slot_new(channel)
```

Allocates and initializes a new slot for use with the channel. If this is the first slot in the channel, it will automatically be added to the channel as the first slot. For all subsequent calls on a given channel, the slot will need to be added to the channel via. the [`aws_channel_slot_insert_right`](@ref)(), [`aws_channel_slot_insert_end`](@ref)(), and [`aws_channel_slot_insert_left`](@ref)() APIs.

### Prototype

```c
struct aws_channel_slot *aws_channel_slot_new(struct aws_channel *channel);
```
