```
aws_http2_connection_ping(http2_connection, optional_opaque_data, on_completed, user_data)
```

Send a PING frame (HTTP/2 only). Round-trip-time is calculated when PING ACK is received from peer.

# Arguments

  * `http2_connection`: HTTP/2 connection.
  * `optional_opaque_data`: Optional payload for PING frame. Must be NULL, or exactly 8 bytes ([`AWS_HTTP2_PING_DATA_SIZE`](@ref)). If NULL, the 8 byte payload will be all zeroes.
  * `on_completed`: Optional callback, invoked when PING ACK is received from peer, or when a connection error prevents the PING ACK from being received. Callback always fires on the connection's event-loop thread.
  * `user_data`: User-data pass to on_completed callback.

### Prototype

```c
int aws_http2_connection_ping( struct aws_http_connection *http2_connection, const struct aws_byte_cursor *optional_opaque_data, aws_http2_on_ping_complete_fn *on_completed, void *user_data);
```
