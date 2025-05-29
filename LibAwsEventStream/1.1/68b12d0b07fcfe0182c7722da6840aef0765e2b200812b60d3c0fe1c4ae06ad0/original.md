```
aws_event_stream_streaming_decoder_init(decoder, alloc, on_payload_segment, on_prelude, on_header, on_error, user_data)
```

Deprecated. Use [`aws_event_stream_streaming_decoder_init_from_options`](@ref) instead. Initialize a streaming decoder for messages with callbacks for usage and an optional user context pointer.

### Prototype

```c
void aws_event_stream_streaming_decoder_init( struct aws_event_stream_streaming_decoder *decoder, struct aws_allocator *alloc, aws_event_stream_process_on_payload_segment_fn *on_payload_segment, aws_event_stream_prelude_received_fn *on_prelude, aws_event_stream_header_received_fn *on_header, aws_event_stream_on_error_fn *on_error, void *user_data);
```
