```
aws_event_stream_message_to_debug_str(fd, message)
```

Writes the message to fd in json format. All strings and binary fields are base64 encoded.

### Prototype

```c
int aws_event_stream_message_to_debug_str( FILE *fd, const struct aws_event_stream_message *message);
```
