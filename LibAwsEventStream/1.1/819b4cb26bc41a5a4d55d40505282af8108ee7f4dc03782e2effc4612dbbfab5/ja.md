```
aws_event_stream_message_init(message, alloc, headers, payload)
```

ヘッダーのリスト、ペイロード、およびペイロードの長さで初期化します。CRCは自動的に計算されます。ヘッダーまたはペイロードがNULLの場合、フィールドは適切に設定され、ヘッダーなしおよび/またはペイロードなしを示します。ペイロードとヘッダーの両方が割り当てを引き起こします。

### プロトタイプ

```c
int aws_event_stream_message_init( struct aws_event_stream_message *message, struct aws_allocator *alloc, const struct aws_array_list *headers, const struct aws_byte_buf *payload);
```
