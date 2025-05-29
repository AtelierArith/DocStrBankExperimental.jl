```
aws_channel_slot_acquire_max_message_for_write(slot)
```

Convenience function that invokes [`aws_channel_acquire_message_from_pool`](@ref)(), asking for the largest reasonable DATA message that can be sent in the write direction, with upstream overhead accounted for. This cannot fail, it never returns NULL.

### Prototype

```c
struct aws_io_message *aws_channel_slot_acquire_max_message_for_write(struct aws_channel_slot *slot);
```
