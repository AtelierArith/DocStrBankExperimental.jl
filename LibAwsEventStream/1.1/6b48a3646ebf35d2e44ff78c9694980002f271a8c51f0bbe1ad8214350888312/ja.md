```
aws_event_stream_message_from_buffer(message, alloc, buffer)
```

ゼロアロケーション、ゼロコピー。メッセージは単にバッファをラップします。メッセージ関数は、バッファが参照可能なメモリである限りのみ有用です。

### プロトタイプ

```c
int aws_event_stream_message_from_buffer( struct aws_event_stream_message *message, struct aws_allocator *alloc, struct aws_byte_buf *buffer);
```
