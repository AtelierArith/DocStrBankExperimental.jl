```
aws_message_pool_acquire(msg_pool, message_type, size_hint)
```

Acquires a message from the pool if available, otherwise, it attempts to allocate. If a message is acquired, note that size_hint is just a hint. the return value's capacity will be set to the actual buffer size.

### Prototype

```c
struct aws_io_message *aws_message_pool_acquire( struct aws_message_pool *msg_pool, enum aws_io_message_type message_type, size_t size_hint);
```
