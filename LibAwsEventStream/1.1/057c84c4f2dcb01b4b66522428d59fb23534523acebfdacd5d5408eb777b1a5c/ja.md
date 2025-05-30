```
aws_event_stream_headers_list_init(headers, allocator)
```

ヘッダーリストを初期化します。動的モードでは、デフォルトで容量は4になります。

### プロトタイプ

```c
int aws_event_stream_headers_list_init( struct aws_array_list *headers, struct aws_allocator *allocator);
```
