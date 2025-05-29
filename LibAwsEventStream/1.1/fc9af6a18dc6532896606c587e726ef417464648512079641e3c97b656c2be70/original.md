```
aws_event_stream_write_headers_to_buffer_safe(headers, buf)
```

Writes headers to buf assuming buf is large enough to hold the data. Prefer this function over the unsafe variant '[`aws_event_stream_write_headers_to_buffer`](@ref)'.

Returns AWS_OP_SUCCESS if the headers were successfully and completely written and AWS_OP_ERR otherwise.

### Prototype

```c
int aws_event_stream_write_headers_to_buffer_safe( const struct aws_array_list *headers, struct aws_byte_buf *buf);
```
