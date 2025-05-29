```
aws_socket_shutdown_dir(socket, dir)
```

Calls `shutdown()` on the socket based on direction.

### Prototype

```c
int aws_socket_shutdown_dir(struct aws_socket *socket, enum aws_channel_direction dir);
```
