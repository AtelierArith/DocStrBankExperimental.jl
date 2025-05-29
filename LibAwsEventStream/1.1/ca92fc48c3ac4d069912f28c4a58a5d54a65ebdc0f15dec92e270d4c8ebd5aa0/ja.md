```
aws_event_stream_add_int16_header(headers, name, name_len, value)
```

は、ヘッダーのリストに16ビット整数を追加します。

### プロトタイプ

```c
int aws_event_stream_add_int16_header( struct aws_array_list *headers, const char *name, uint8_t name_len, int16_t value);
```
