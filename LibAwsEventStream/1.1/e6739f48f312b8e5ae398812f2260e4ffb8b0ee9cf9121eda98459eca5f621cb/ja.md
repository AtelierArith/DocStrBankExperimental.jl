```
aws_event_stream_message_message_crc(message)
```

メッセージ全体のチェックサムを返します (crc32)

### プロトタイプ

```c
uint32_t aws_event_stream_message_message_crc(const struct aws_event_stream_message *message);
```
