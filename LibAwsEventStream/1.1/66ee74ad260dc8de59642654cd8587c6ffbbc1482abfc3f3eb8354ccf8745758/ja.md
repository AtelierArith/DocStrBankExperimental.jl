```
aws_event_stream_streaming_decoder_clean_up(decoder)
```

現在、aws*aws*event*stream*streaming_decoder内ではメモリは割り当てられていませんが、将来のAPI互換性のために、使用が終わったらこれを呼び出すべきです。

### プロトタイプ

```c
void aws_event_stream_streaming_decoder_clean_up( struct aws_event_stream_streaming_decoder *decoder);
```
