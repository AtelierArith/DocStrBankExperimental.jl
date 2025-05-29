```
aws_socket_start_accept(socket, accept_loop, options)
```

TCP, LOCAL and VSOCK only. The socket will begin accepting new connections. This is an asynchronous operation. New connections or errors will arrive via the `on_accept_result` callback.

[`aws_socket_bind`](@ref)() and [`aws_socket_listen`](@ref)() must be called before calling this function.

### Prototype

```c
int aws_socket_start_accept( struct aws_socket *socket, struct aws_event_loop *accept_loop, struct aws_socket_listener_options options);
```
