```
aws_pipe_read(read_end, dst_buffer, num_bytes_read)
```

Read data from the pipe into the destination buffer. Attempts to read enough to fill all remaining space in the buffer, from `dst\_buffer->len` to `dst\_buffer->capacity`. `dst\_buffer->len` is updated to reflect the buffer's new length. `num_bytes_read` (optional) is set to the total number of bytes read. This function never blocks. If no bytes could be read without blocking, then AWS_OP_ERR is returned and aws_last_error() code will be AWS_IO_READ_WOULD_BLOCK. This must be called on the thread of the connected event-loop.

### Prototype

```c
int aws_pipe_read(struct aws_pipe_read_end *read_end, struct aws_byte_buf *dst_buffer, size_t *num_bytes_read);
```
