```
aws_async_input_stream_read_to_fill(stream, dest)
```

Read repeatedly from the async stream until the buffer is full, or EOF is reached. Depending on implementation, this could complete at any time. It may complete synchronously. It may complete on another thread. Returns a future, which will contain an error code if something went wrong, or a result bool indicating whether EOF has been reached.

WARNING: The buffer must have space available. WARNING: Do not read again until the previous read is complete.

### Prototype

```c
struct aws_future_bool *aws_async_input_stream_read_to_fill( struct aws_async_input_stream *stream, struct aws_byte_buf *dest);
```
