```
aws_socket_channel_bootstrap_options
```

Socket-based channel creation options.

bootstrap - configs name resolution and which event loop group the connection will be seated into host_name - host to connect to; if a dns address, will be resolved prior to connecting port - port to connect to socket_options - socket properties, including type (tcp vs. udp vs. unix domain) and connect timeout. TLS connections are currently restricted to tcp (AWS_SOCKET_STREAM) only. tls_options - (optional) tls context to apply after connection establishment. If NULL, the connection will not be protected by TLS. creation_callback - (optional) callback invoked when the channel is first created. This is always right after the connection was successfully established. *Does NOT* get called if the initial connect failed. setup_callback - callback invoked once the channel is ready for use and TLS has been negotiated or if an error is encountered shutdown_callback - callback invoked once the channel has shutdown. enable_read_back_pressure - controls whether or not back pressure will be applied in the channel user_data - arbitrary data to pass back to the various callbacks requested_event_loop - if set, the connection will be placed on the requested event loop rather than one chosen internally from the bootstrap's associated event loop group. It is an error to pass in an event loop that is not associated with the bootstrap's event loop group.

Immediately after the `shutdown_callback` returns, the channel is cleaned up automatically. All callbacks are invoked in the thread of the event-loop that the new channel is assigned to.
