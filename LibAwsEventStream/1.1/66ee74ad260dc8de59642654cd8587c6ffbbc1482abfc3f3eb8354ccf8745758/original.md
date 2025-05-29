```
aws_event_stream_streaming_decoder_clean_up(decoder)
```

Currently, no memory is allocated inside aws_aws_event_stream_streaming_decoder, but for future API compatibility, you should call this when finished with it.

### Prototype

```c
void aws_event_stream_streaming_decoder_clean_up( struct aws_event_stream_streaming_decoder *decoder);
```
