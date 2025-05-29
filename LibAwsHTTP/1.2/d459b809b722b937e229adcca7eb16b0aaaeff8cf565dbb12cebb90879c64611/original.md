```
aws_http2_connection_send_goaway(http2_connection, http2_error, allow_more_streams, optional_debug_data)
```

Send a custom GOAWAY frame (HTTP/2 only).

Note that the connection automatically attempts to send a GOAWAY during shutdown (unless a GOAWAY with a valid Last-Stream-ID has already been sent).

This call can be used to gracefully warn the peer of an impending shutdown (http2_error=0, allow_more_streams=true), or to customize the final GOAWAY frame that is sent by this connection.

The other end may not receive the goaway, if the connection already closed.

# Arguments

  * `http2_connection`: HTTP/2 connection.
  * `http2_error`: The HTTP/2 error code (RFC-7540 section 7) to send. `enum [`aws*http2*error_code`](@ref)` lists official codes.
  * `allow_more_streams`: If true, new peer-initiated streams will continue to be acknowledged and the GOAWAY's Last-Stream-ID will be set to a max value. If false, new peer-initiated streams will be ignored and the GOAWAY's Last-Stream-ID will be set to the latest acknowledged stream.
  * `optional_debug_data`: Optional debug data to send. Size must not exceed 16KB.

### Prototype

```c
void aws_http2_connection_send_goaway( struct aws_http_connection *http2_connection, uint32_t http2_error, bool allow_more_streams, const struct aws_byte_cursor *optional_debug_data);
```
