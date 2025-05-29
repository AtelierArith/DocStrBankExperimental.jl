```
aws_event_stream_header_name(header)
```

ヘッダー名を返します。注意: この値はヌル終端されていません

### プロトタイプ

```c
struct aws_byte_buf aws_event_stream_header_name( struct aws_event_stream_header_value_pair *header);
```
