```
aws_http_stream_acquire(stream)
```

Acquire refcount on the stream to prevent it from being cleaned up until it is released.

### Prototype

```c
struct aws_http_stream *aws_http_stream_acquire(struct aws_http_stream *stream);
```
