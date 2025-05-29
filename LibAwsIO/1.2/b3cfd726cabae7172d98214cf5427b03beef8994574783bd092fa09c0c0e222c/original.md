```
aws_socket_stop_accept(socket)
```

TCP, LOCAL and VSOCK only. The listening socket will stop accepting new connections. It is safe to call `[`aws*socket*start_accept`](@ref)()` again after this operation. This can be called from any thread but be aware, on some platforms, if you call this from outside of the current event loop's thread, it will block until the event loop finishes processing the request for unsubscribe in it's own thread.

### Prototype

```c
int aws_socket_stop_accept(struct aws_socket *socket);
```
