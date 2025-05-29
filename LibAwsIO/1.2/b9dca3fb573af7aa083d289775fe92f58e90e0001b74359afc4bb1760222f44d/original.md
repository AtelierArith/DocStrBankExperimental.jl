```
aws_channel_new(allocator, creation_args)
```

Allocates new channel, Unless otherwise specified all functions for channels and channel slots must be executed within that channel's event-loop's thread. channel_options are copied.

### Prototype

```c
struct aws_channel *aws_channel_new(struct aws_allocator *allocator, const struct aws_channel_options *creation_args);
```
