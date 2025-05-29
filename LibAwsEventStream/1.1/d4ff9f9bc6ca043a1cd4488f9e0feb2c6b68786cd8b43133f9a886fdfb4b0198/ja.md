```
aws_event_stream_message_from_buffer_copy(message, alloc, buffer)
```

メモリを割り当ててバッファをコピーします。それ以外は aws*aws*event*stream*message*from*buffer と同じです。これは遅くなりますが、より安全である可能性があります。

### プロトタイプ

```c
int aws_event_stream_message_from_buffer_copy( struct aws_event_stream_message *message, struct aws_allocator *alloc, const struct aws_byte_buf *buffer);
```
