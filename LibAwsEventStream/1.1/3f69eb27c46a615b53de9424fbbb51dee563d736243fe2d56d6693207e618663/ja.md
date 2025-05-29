```
aws_event_stream_add_timestamp_header(headers, name, name_len, value)
```

は、Unixエポックからのミリ秒を表す64ビット整数をヘッダーのリストに追加します。

### プロトタイプ

```c
int aws_event_stream_add_timestamp_header( struct aws_array_list *headers, const char *name, uint8_t name_len, int64_t value);
```
