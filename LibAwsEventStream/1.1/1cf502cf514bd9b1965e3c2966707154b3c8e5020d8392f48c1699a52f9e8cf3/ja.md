```
aws_event_stream_add_uuid_header(headers, name, name_len, value)
```

ヘッダーのリストにUUIDバッファを追加します。値は常に16バイトの長さでなければなりません。

### プロトタイプ

```c
int aws_event_stream_add_uuid_header( struct aws_array_list *headers, const char *name, uint8_t name_len, const uint8_t *value);
```
