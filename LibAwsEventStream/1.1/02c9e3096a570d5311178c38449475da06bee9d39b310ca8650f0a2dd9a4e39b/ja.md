```
aws_event_stream_channel_handler_new(allocator, handler_options)
```

[`aws_event_stream_message`](@ref)() イベントを処理するための新しいチャネルハンドラーを割り当てて初期化します。ハンドラーオプションは null であってはなりません。

### プロトタイプ

```c
struct aws_channel_handler *aws_event_stream_channel_handler_new( struct aws_allocator *allocator, const struct aws_event_stream_channel_handler_options *handler_options);
```
