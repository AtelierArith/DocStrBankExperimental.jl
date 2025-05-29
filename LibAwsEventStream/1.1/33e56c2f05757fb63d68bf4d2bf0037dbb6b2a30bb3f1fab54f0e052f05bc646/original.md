```
aws_event_stream_streaming_decoder_init_from_options(decoder, allocator, options)
```

Initialize a streaming decoder for messages with callbacks for usage and an optional user context pointer.

### Prototype

```c
void aws_event_stream_streaming_decoder_init_from_options( struct aws_event_stream_streaming_decoder *decoder, struct aws_allocator *allocator, const struct aws_event_stream_streaming_decoder_options *options);
```
