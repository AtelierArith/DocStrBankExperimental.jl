```
aws_server_bootstrap_new_socket_listener(bootstrap_options)
```

Sets up a server socket listener. If you are planning on using TLS, use `aws_server_bootstrap_new_tls_socket_listener` instead. This creates a socket listener bound to `local_endpoint` using socket options `options`. `incoming_callback` will be invoked once an incoming channel is ready for use or if an error is encountered. `shutdown_callback` will be invoked once the channel has shutdown. `destroy_callback` will be invoked after the server socket listener is destroyed, and all associated connections and channels have finished shutting down. Immediately after the `shutdown_callback` returns, the channel is cleaned up automatically. All callbacks are invoked the thread of the event-loop that the listening socket is assigned to

`setup_callback`. If set, the callback will be asynchronously invoked when the listener is ready for use. For Apple Network Framework, the listener is not usable until the callback is invoked. If the listener creation failed (return NULL), the `setup_callback` will not be invoked.

Upon shutdown of your application, you'll want to call [`aws_server_bootstrap_destroy_socket_listener`](@ref) with the return value from this function.

bootstrap_options is copied.

### Prototype

```c
struct aws_socket *aws_server_bootstrap_new_socket_listener( const struct aws_server_socket_channel_bootstrap_options *bootstrap_options);
```
