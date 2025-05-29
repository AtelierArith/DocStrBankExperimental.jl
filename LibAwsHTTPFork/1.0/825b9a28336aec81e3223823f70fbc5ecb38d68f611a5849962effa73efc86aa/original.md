```
aws_http2_connection_get_sent_goaway(http2_connection, out_http2_error, out_last_stream_id)
```

Get data about the latest GOAWAY frame sent to peer (HTTP/2 only). If no GOAWAY has been sent, AWS_ERROR_HTTP_DATA_NOT_AVAILABLE will be raised. Note that GOAWAY frames are typically sent automatically by the connection during shutdown.

# Arguments

  * `http2_connection`: HTTP/2 connection.
  * `out_http2_error`: Gets set to HTTP/2 error code sent in most recent GOAWAY.
  * `out_last_stream_id`: Gets set to Last-Stream-ID sent in most recent GOAWAY.

### Prototype

```c
int aws_http2_connection_get_sent_goaway( struct aws_http_connection *http2_connection, uint32_t *out_http2_error, uint32_t *out_last_stream_id);
```
