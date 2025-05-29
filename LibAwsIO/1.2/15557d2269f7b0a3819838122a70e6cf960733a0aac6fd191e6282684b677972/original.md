```
aws_async_input_stream_release(stream)
```

Decrement reference count. You may pass in NULL (has no effect). Always returns NULL.

### Prototype

```c
struct aws_async_input_stream *aws_async_input_stream_release(struct aws_async_input_stream *stream);
```
