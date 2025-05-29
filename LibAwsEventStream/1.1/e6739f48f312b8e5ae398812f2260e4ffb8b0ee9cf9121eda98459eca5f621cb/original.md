```
aws_event_stream_message_message_crc(message)
```

Returns the checksum of the entire message (crc32)

### Prototype

```c
uint32_t aws_event_stream_message_message_crc(const struct aws_event_stream_message *message);
```
