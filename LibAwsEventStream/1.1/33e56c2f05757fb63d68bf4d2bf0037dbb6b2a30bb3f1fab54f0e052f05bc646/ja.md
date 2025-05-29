```
aws_event_stream_streaming_decoder_init_from_options(decoder, allocator, options)
```

コールバックを使用するメッセージのストリーミングデコーダを初期化し、オプションのユーザーコンテキストポインタを設定します。

### プロトタイプ

```c
void aws_event_stream_streaming_decoder_init_from_options( struct aws_event_stream_streaming_decoder *decoder, struct aws_allocator *allocator, const struct aws_event_stream_streaming_decoder_options *options);
```
