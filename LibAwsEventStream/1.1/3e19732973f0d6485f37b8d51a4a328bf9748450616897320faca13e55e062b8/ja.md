```
aws_event_stream_channel_handler_increment_read_window(handler, window_update_size)
```

チャネルの読み取りウィンドウを更新します。automatic*window*managementがfalseに設定されている場合に限ります。

### プロトタイプ

```c
void aws_event_stream_channel_handler_increment_read_window( struct aws_channel_handler *handler, size_t window_update_size);
```
