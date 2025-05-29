```
aws_event_stream_add_bytebuf_header(headers, name, name_len, value, value_len, copy)
```

バイトバッファヘッダーをヘッダーのリストに追加します。copyがtrueに設定されている場合、これはヘッダー値のためのメモリ割り当てを引き起こします。そうでない場合、値は'value'のメモリアドレスに設定されます。

### プロトタイプ

```c
int aws_event_stream_add_bytebuf_header( struct aws_array_list *headers, const char *name, uint8_t name_len, uint8_t *value, uint16_t value_len, int8_t copy);
```
