```
aws_message_pool_init(msg_pool, alloc, args)
```

Initializes message pool using 'msg_pool' as the backing pool, 'args' is copied.

### Prototype

```c
int aws_message_pool_init( struct aws_message_pool *msg_pool, struct aws_allocator *alloc, struct aws_message_pool_creation_args *args);
```
