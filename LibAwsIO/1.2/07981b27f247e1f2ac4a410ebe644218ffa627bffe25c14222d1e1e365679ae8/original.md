```
aws_server_socket_channel_bootstrap_options
```

Arguments to setup a server socket listener which will also negotiate and configure TLS. This creates a socket listener bound to `host` and 'port' using socket options `options`, and TLS options `tls_options`. `incoming_callback` will be invoked once an incoming channel is ready for use and TLS is finished negotiating, or if an error is encountered. `shutdown_callback` will be invoked once the channel has shutdown. `destroy_callback` will be invoked after the server socket listener is destroyed, and all associated connections and channels have finished shutting down. Immediately after the `shutdown_callback` returns, the channel is cleaned up automatically. All callbacks are invoked in the thread of the event-loop that listener is assigned to.

Upon shutdown of your application, you'll want to call [`aws_server_bootstrap_destroy_socket_listener`](@ref) with the return value from this function.

The socket type in `options` must be AWS_SOCKET_STREAM if tls_options is set. DTLS is not currently supported for tls.
