```
aws_event_stream_streaming_decoder_init(decoder, alloc, on_payload_segment, on_prelude, on_header, on_error, user_data)
```

非推奨。代わりに [`aws_event_stream_streaming_decoder_init_from_options`](@ref) を使用してください。コールバックとオプションのユーザーコンテキストポインタを使用して、メッセージのストリーミングデコーダを初期化します。

### プロトタイプ

```c
void aws_event_stream_streaming_decoder_init( struct aws_event_stream_streaming_decoder *decoder, struct aws_allocator *alloc, aws_event_stream_process_on_payload_segment_fn *on_payload_segment, aws_event_stream_prelude_received_fn *on_prelude, aws_event_stream_header_received_fn *on_header, aws_event_stream_on_error_fn *on_error, void *user_data);
```
