```
aws_event_stream_headers_list_init(headers, allocator)
```

initializes a headers list for you. It will default to a capacity of 4 in dynamic mode.

### Prototype

```c
int aws_event_stream_headers_list_init( struct aws_array_list *headers, struct aws_allocator *allocator);
```
