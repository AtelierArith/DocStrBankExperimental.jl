```
aws_event_stream_add_bool_header_by_cursor(headers, name, value)
```

ブール値のヘッダーをヘッダーリストに追加します

# 引数

  * `headers`: 追加するヘッダーリスト
  * `name`: 追加するヘッダーの名前
  * `value`: 追加するヘッダーの値

# 戻り値

成功時は AWS*OP*SUCCESS、失敗時は AWS*OP*ERR

### プロトタイプ

```c
int aws_event_stream_add_bool_header_by_cursor( struct aws_array_list *headers, struct aws_byte_cursor name, bool value);
```
