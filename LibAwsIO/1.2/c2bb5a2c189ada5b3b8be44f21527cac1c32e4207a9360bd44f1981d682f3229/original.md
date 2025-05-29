```
aws_socket_listen(socket, backlog_size)
```

TCP, LOCAL and VSOCK only. Sets up the socket to listen on the address bound to in `[`aws*socket*bind`](@ref)()`.

### Prototype

```c
int aws_socket_listen(struct aws_socket *socket, int backlog_size);
```
