```
aws_event_stream_add_header(headers, header)
```

一般的なヘッダーをヘッダーのリストに追加します。基になるデータのコピーを作成します。

### プロトタイプ

```c
int aws_event_stream_add_header( struct aws_array_list *headers, const struct aws_event_stream_header_value_pair *header);
```
