Invoked when an HTTP/2 GOAWAY frame is received from peer. Implies that the peer has initiated shutdown, or encountered a serious error. Once a GOAWAY is received, no further streams may be created on this connection.

# Arguments

  * `http2_connection`: This HTTP/2 connection.
  * `last_stream_id`: ID of the last locally-initiated stream that peer will process. Any locally-initiated streams with a higher ID are ignored by peer, and are safe to retry on another connection.
  * `http2_error_code`: The HTTP/2 error code (RFC-7540 section 7) sent by peer. `enum [`aws*http2*error_code`](@ref)` lists official codes.
  * `debug_data`: The debug data sent by peer. It can be empty. (NOTE: this data is only valid for the lifetime of the callback. Make a deep copy if you wish to keep it longer.)
  * `user_data`: User-data passed to the callback.
