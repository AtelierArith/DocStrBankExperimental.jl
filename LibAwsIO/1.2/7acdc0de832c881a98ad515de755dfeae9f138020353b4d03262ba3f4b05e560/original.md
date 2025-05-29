```
aws_server_bootstrap_destroy_socket_listener(bootstrap, listener)
```

Shuts down 'listener' and cleans up any resources associated with it. Any incoming channels on `listener` will still be active. `destroy_callback` will be invoked after the server socket listener is destroyed, and all associated connections and channels have finished shutting down.

### Prototype

```c
void aws_server_bootstrap_destroy_socket_listener( struct aws_server_bootstrap *bootstrap, struct aws_socket *listener);
```
