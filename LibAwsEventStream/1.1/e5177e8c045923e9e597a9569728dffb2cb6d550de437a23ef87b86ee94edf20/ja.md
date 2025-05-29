```
aws_event_stream_message_to_debug_str(fd, message)
```

メッセージをfdにjson形式で書き込みます。すべての文字列とバイナリフィールドはbase64エンコードされています。

### プロトタイプ

```c
int aws_event_stream_message_to_debug_str( FILE *fd, const struct aws_event_stream_message *message);
```
