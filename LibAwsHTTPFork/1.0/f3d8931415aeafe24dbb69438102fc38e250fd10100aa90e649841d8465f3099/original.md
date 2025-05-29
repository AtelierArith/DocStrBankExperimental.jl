```
aws_http2_stream_get_received_reset_error_code(http2_stream, out_http2_error)
```

Get the error code received in rst_stream. Only valid if the stream has completed, and an RST_STREAM frame has received.

# Arguments

  * `http2_stream`: HTTP/2 stream.
  * `out_http2_error`: Gets to set to HTTP/2 error code received in rst_stream.

### Prototype

```c
int aws_http2_stream_get_received_reset_error_code(struct aws_http_stream *http2_stream, uint32_t *out_http2_error);
```
