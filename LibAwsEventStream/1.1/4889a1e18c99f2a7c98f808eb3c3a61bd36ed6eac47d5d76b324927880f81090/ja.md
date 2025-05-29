```
aws_event_stream_header_value_length(header)
```

ヘッダー値バッファの長さを返します。これは主に文字列およびバイトバッファタイプを対象としています。

### プロトタイプ

```c
uint16_t aws_event_stream_header_value_length(struct aws_event_stream_header_value_pair *header);
```
