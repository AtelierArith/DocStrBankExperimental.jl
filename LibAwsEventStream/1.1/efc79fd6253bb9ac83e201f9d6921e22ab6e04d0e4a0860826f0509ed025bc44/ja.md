```
aws_event_stream_add_byte_header(headers, name, name_len, value)
```

バイトヘッダーをヘッダーのリストに追加します。

### プロトタイプ

```c
int aws_event_stream_add_byte_header( struct aws_array_list *headers, const char *name, uint8_t name_len, int8_t value);
```
