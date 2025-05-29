```
aws_event_stream_message_payload(message)
```

メッセージペイロードの先頭へのポインタを返します。

### プロトタイプ

```c
const uint8_t *aws_event_stream_message_payload(const struct aws_event_stream_message *message);
```
