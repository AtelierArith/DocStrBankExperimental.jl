```
aws_event_stream_add_int64_header(headers, name, name_len, value)
```

64ビット整数をヘッダーのリストに追加します。

### プロトタイプ

```c
int aws_event_stream_add_int64_header( struct aws_array_list *headers, const char *name, uint8_t name_len, int64_t value);
```
