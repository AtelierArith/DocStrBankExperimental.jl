```
aws_event_stream_streaming_decoder_pump(decoder, data)
```

デコーダの主要なドライバーです。デコードされるべきデータとその長さを渡します。ここでの一般的な使用例は、ioデバイスからの読み取りイベントに応じてです。

### プロトタイプ

```c
int aws_event_stream_streaming_decoder_pump( struct aws_event_stream_streaming_decoder *decoder, const struct aws_byte_buf *data);
```
