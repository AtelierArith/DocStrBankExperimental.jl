```
aws_event_stream_header_value_as_uuid(header)
```

ヘッダー値を返します。これは16バイトの長さのバイトバッファで、UUIDを表します。

### プロトタイプ

```c
struct aws_byte_buf aws_event_stream_header_value_as_uuid( struct aws_event_stream_header_value_pair *header);
```
