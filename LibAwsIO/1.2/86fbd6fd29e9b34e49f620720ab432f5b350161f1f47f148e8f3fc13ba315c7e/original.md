```
aws_socket_set_cleanup_complete_callback(socket, fn, user_data)
```

Apple Network Framework only. The callback that will triggered when aws_socket_cleanup() finished. And it is only safe to release the socket afterwards. The callback will be called from the socket event loop.

### Prototype

```c
int aws_socket_set_cleanup_complete_callback( struct aws_socket *socket, aws_socket_on_shutdown_complete_fn fn, void *user_data);
```
