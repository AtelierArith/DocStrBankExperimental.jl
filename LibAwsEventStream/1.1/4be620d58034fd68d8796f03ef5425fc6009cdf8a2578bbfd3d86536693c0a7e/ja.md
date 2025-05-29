```
aws_event_stream_add_bool_header(headers, name, name_len, value)
```

ブールヘッダーをヘッダーのリストに追加します。

### プロトタイプ

```c
int aws_event_stream_add_bool_header( struct aws_array_list *headers, const char *name, uint8_t name_len, int8_t value);
```
