```
aws_async_input_stream_read(stream, dest)
```

非同期ストリームからバッファに1回読み込みます。読み込みは、少なくとも1バイトが読み込まれたとき、バッファが満杯になったとき、またはEOFに達したときに完了します。実装によっては、読み込みはいつでも完了する可能性があります。同期的に完了する場合もあれば、別のスレッドで完了する場合もあります。何か問題が発生した場合はエラーコードを含む未来を返し、EOFに達したかどうかを示す結果のboolを返します。

警告: バッファには空きが必要です。警告: 前の読み込みが完了するまで再度読み込まないでください。

### プロトタイプ

```c
struct aws_future_bool *aws_async_input_stream_read(struct aws_async_input_stream *stream, struct aws_byte_buf *dest);
```
