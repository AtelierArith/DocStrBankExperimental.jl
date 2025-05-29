```
aws_event_stream_header_value_as_bytebuf(header)
```

ヘッダー値をバイトバッファへのポインタとして返します。バッファの長さを決定するには、[`aws_event_stream_header_value_length`](@ref)を呼び出してください。

### プロトタイプ

```c
struct aws_byte_buf aws_event_stream_header_value_as_bytebuf( struct aws_event_stream_header_value_pair *header);
```
