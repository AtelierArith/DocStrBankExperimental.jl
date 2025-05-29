```
aws_socket_bind(socket, socket_bind_options)
```

Binds the socket to a local address. In UDP mode, the socket is ready for `[`aws*socket*read`](@ref)()` operations. In connection oriented modes, you still must call `[`aws*socket*listen`](@ref)()` and `[`aws*socket*start*accept`](@ref)()` before using the socket. local\*endpoint is copied.

### Prototype

```c
int aws_socket_bind(struct aws_socket *socket, struct aws_socket_bind_options *socket_bind_options);
```
