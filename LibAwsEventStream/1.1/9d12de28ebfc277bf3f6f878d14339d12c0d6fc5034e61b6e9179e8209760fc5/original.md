```
aws_event_stream_streaming_decoder_pump(decoder, data)
```

The main driver of the decoder. Pass data that should be decoded with its length. A likely use-case here is in response to a read event from an io-device

### Prototype

```c
int aws_event_stream_streaming_decoder_pump( struct aws_event_stream_streaming_decoder *decoder, const struct aws_byte_buf *data);
```
