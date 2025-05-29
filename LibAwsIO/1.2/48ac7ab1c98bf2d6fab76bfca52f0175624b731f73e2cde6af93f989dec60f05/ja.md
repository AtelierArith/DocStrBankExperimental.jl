```
aws_channel_handler_increment_read_window(handler, slot, size)
```

ハンドラーのvtableでon*window*updateを呼び出します。

### プロトタイプ

```c
int aws_channel_handler_increment_read_window( struct aws_channel_handler *handler, struct aws_channel_slot *slot, size_t size);
```
