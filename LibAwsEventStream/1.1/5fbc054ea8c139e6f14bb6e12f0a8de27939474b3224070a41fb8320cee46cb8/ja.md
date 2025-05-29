```
aws_event_stream_header_value_as_string(header)
```

ヘッダー値を文字列として返します。注意: この値はヌル終端ではありません。

### プロトタイプ

```c
struct aws_byte_buf aws_event_stream_header_value_as_string( struct aws_event_stream_header_value_pair *header);
```
