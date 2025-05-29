```
aws_event_stream_message_clean_up(message)
```

Cleans up any internally allocated memory. Always call this for API compatibility reasons, even if you only used the aws_aws_event_stream_message_from_buffer function.

### Prototype

```c
void aws_event_stream_message_clean_up(struct aws_event_stream_message *message);
```
