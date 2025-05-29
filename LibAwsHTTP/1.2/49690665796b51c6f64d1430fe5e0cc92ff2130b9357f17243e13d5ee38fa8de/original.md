```
aws_http_stream_cancel(stream, error_code)
```

Cancel the stream in flight. For HTTP/1.1 streams, it's equivalent to closing the connection. For HTTP/2 streams, it's equivalent to calling reset on the stream with `AWS_HTTP2_ERR_CANCEL`.

the stream will complete with the error code provided, unless the stream is already completing for other reasons, or the stream is not activated, in which case this call will have no impact.

### Prototype

```c
void aws_http_stream_cancel(struct aws_http_stream *stream, int error_code);
```
