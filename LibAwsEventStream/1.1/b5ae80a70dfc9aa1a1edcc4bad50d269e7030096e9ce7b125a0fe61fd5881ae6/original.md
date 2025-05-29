```
aws_event_stream_read_headers_from_buffer(headers, buffer, headers_len)
```

Get the headers from the buffer, store them in the headers list. the user's responsibility to cleanup the list when they are finished with it. no buffer copies happen here, the lifetime of the buffer, must outlive the usage of the headers. returns error codes defined in the public interface.

### Prototype

```c
int aws_event_stream_read_headers_from_buffer( struct aws_array_list *headers, const uint8_t *buffer, size_t headers_len);
```
