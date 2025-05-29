```
aws_socket_subscribe_to_readable_events(socket, on_readable, user_data)
```

Subscribes on_readable to notifications when the socket goes readable (edge-triggered). Errors will also be received in the callback.

Note! This function is technically not thread safe, but we do not enforce which thread you call from. It's your responsibility to either call this in safely (e.g. just don't call it in parallel from multiple threads) or schedule a task to call it. If you call it before your first call to read, it will be fine.

### Prototype

```c
int aws_socket_subscribe_to_readable_events( struct aws_socket *socket, aws_socket_on_readable_fn *on_readable, void *user_data);
```
