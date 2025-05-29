```
aws_socket_set_close_complete_callback(socket, fn, user_data)
```

Apple Network Framework only. The callback that will triggered when [`aws_socket_close`](@ref)() finished. The callback will be called from the socket event loop.

### Prototype

```c
int aws_socket_set_close_complete_callback( struct aws_socket *socket, aws_socket_on_shutdown_complete_fn fn, void *user_data);
```
