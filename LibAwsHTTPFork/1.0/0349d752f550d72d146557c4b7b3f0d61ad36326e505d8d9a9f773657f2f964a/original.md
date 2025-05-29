```
aws_http2_stream_reset(http2_stream, http2_error)
```

Reset the HTTP/2 stream (HTTP/2 only). Note that if the stream closes before this async call is fully processed, the RST_STREAM frame will not be sent.

# Arguments

  * `http2_stream`: HTTP/2 stream.
  * `http2_error`: [`aws_http2_error_code`](@ref). Reason to reset the stream.

### Prototype

```c
int aws_http2_stream_reset(struct aws_http_stream *http2_stream, uint32_t http2_error);
```
