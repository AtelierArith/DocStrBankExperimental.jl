```
aws_async_input_stream_read(stream, dest)
```

Read once from the async stream into the buffer. The read completes when at least 1 byte is read, the buffer is full, or EOF is reached. Depending on implementation, the read could complete at any time. It may complete synchronously. It may complete on another thread. Returns a future, which will contain an error code if something went wrong, or a result bool indicating whether EOF has been reached.

WARNING: The buffer must have space available. WARNING: Do not read again until the previous read is complete.

### Prototype

```c
struct aws_future_bool *aws_async_input_stream_read(struct aws_async_input_stream *stream, struct aws_byte_buf *dest);
```
