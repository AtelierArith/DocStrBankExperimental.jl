```
aws_async_input_stream_acquire(stream)
```

Increment reference count. You may pass in NULL (has no effect). Returns whatever pointer was passed in.

### Prototype

```c
struct aws_async_input_stream *aws_async_input_stream_acquire(struct aws_async_input_stream *stream);
```
