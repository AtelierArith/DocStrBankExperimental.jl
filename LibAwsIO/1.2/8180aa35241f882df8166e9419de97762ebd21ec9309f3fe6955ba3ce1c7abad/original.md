```
aws_socket_init(socket, alloc, options)
```

Initializes a socket object with socket options. options will be copied.

### Prototype

```c
int aws_socket_init( struct aws_socket *socket, struct aws_allocator *alloc, const struct aws_socket_options *options);
```
