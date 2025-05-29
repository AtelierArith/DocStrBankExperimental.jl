```
aws_socket_handler_new(allocator, socket, slot, max_read_size)
```

Socket handlers should be the first slot/handler in a channel. It interacts directly with the channel's event loop for read and write notifications. max_read_size is the maximum amount of data it will read from the socket before a context switch (a continuation task will be scheduled).

### Prototype

```c
struct aws_channel_handler *aws_socket_handler_new( struct aws_allocator *allocator, struct aws_socket *socket, struct aws_channel_slot *slot, size_t max_read_size);
```
