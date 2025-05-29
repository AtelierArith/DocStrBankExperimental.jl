```
aws_event_stream_write_headers_to_buffer(headers, buffer)
```

Deprecated in favor of '[`aws_event_stream_write_headers_to_buffer_safe`](@ref)' as this API is unsafe.

Writes headers to buffer and returns the length of bytes written to buffer. Assumes buffer is large enough to store the headers.

### Prototype

```c
size_t aws_event_stream_write_headers_to_buffer(const struct aws_array_list *headers, uint8_t *buffer);
```
