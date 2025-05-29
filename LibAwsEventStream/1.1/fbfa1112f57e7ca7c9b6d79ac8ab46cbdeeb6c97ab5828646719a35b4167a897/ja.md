```
aws_event_stream_add_int16_header_by_cursor(headers, name, value)
```

int16値のヘッダーをヘッダーリストに追加します

# 引数

  * `headers`: 追加するヘッダーリスト
  * `name`: 追加するヘッダーの名前
  * `value`: 追加するヘッダーの値

# 戻り値

成功時はAWS*OP*SUCCESS、失敗時はAWS*OP*ERR

### プロトタイプ

```c
int aws_event_stream_add_int16_header_by_cursor( struct aws_array_list *headers, struct aws_byte_cursor name, int16_t value);
```
