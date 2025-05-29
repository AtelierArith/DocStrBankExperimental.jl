```
aws_server_bootstrap_new(allocator, el_group)
```

Initializes the server bootstrap with `allocator` and `el_group`. This object manages listeners, server connections, and channels.

### Prototype

```c
struct aws_server_bootstrap *aws_server_bootstrap_new( struct aws_allocator *allocator, struct aws_event_loop_group *el_group);
```
