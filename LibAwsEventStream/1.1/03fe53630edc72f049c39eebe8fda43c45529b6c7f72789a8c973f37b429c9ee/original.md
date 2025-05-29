```
aws_event_stream_add_header(headers, header)
```

Adds a generic header to the list of headers. Makes a copy of the underlaying data.

### Prototype

```c
int aws_event_stream_add_header( struct aws_array_list *headers, const struct aws_event_stream_header_value_pair *header);
```
