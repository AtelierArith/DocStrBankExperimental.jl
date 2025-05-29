```
aws_async_input_stream_read_to_fill(stream, dest)
```

非同期ストリームからバッファが満杯になるまで、またはEOFに達するまで繰り返し読み取ります。実装によっては、いつでも完了する可能性があります。同期的に完了する場合もあれば、別のスレッドで完了する場合もあります。何か問題が発生した場合はエラーコードを含む未来を返し、EOFに達したかどうかを示す結果のboolを返します。

警告: バッファには空きが必要です。警告: 前の読み取りが完了するまで再度読み取らないでください。

### プロトタイプ

```c
struct aws_future_bool *aws_async_input_stream_read_to_fill( struct aws_async_input_stream *stream, struct aws_byte_buf *dest);
```
