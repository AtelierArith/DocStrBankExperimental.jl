```
aws_event_stream_message_headers(message, headers)
```

Adds the headers for the message to list. The memory in each header is owned as part of the message, do not free it or pass its address around.

### Prototype

```c
int aws_event_stream_message_headers( const struct aws_event_stream_message *message, struct aws_array_list *headers);
```
