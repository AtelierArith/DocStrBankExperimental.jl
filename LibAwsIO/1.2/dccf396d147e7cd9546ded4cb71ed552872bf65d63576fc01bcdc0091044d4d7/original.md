```
aws_socket_connect(socket, socket_connect_options)
```

Connects to a remote endpoint. In UDP, this simply binds the socket to a remote address for use with `[`aws*socket*write`](@ref)()`, and if the operation is successful, the socket can immediately be used for write operations.

In TCP, LOCAL and VSOCK this function will not block. If the return value is successful, then you must wait on the `on\_connection\_result()` callback to be invoked before using the socket.

If an event_loop is provided for UDP sockets, a notification will be sent on on_connection_result in the event-loop's thread. Upon completion, the socket will already be assigned an event loop. If NULL is passed for UDP, it will immediately return upon success, but you must call [`aws_socket_assign_to_event_loop`](@ref) before use.

### Prototype

```c
int aws_socket_connect(struct aws_socket *socket, struct aws_socket_connect_options *socket_connect_options);
```
