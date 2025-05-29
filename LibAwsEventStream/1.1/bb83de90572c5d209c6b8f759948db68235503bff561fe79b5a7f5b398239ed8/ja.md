```
aws_event_stream_library_init(allocator)
```

aws-c-event-streamで使用される内部データ構造を初期化します。aws-c-event-streamの機能を使用する前に呼び出す必要があります。

### プロトタイプ

```c
void aws_event_stream_library_init(struct aws_allocator *allocator);
```
