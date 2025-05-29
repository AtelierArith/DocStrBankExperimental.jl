```
aws_event_stream_headers_list_cleanup(headers)
```

Cleans up the headers list. Also deallocates any headers that were the result of a copy flag for strings or buffer.

### Prototype

```c
void aws_event_stream_headers_list_cleanup(struct aws_array_list *headers);
```
