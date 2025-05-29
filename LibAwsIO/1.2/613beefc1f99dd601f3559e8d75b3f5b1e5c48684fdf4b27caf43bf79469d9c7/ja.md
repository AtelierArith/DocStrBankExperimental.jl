```
aws_pipe_read(read_end, dst_buffer, num_bytes_read)
```

パイプからデータを宛先バッファに読み込みます。バッファの残りのすべてのスペースを埋めるのに十分な量を読み取ろうとし、`dst_buffer->len` から `dst_buffer->capacity` までを対象とします。`dst_buffer->len` はバッファの新しい長さを反映するように更新されます。`num_bytes_read`（オプション）は、読み取られたバイトの合計数に設定されます。この関数は決してブロックしません。ブロックせずにバイトを読み取ることができなかった場合、AWS*OP*ERR が返され、aws*last*error() コードは AWS*IO*READ*WOULD*BLOCK になります。これは接続されたイベントループのスレッドで呼び出す必要があります。

### プロトタイプ

```c
int aws_pipe_read(struct aws_pipe_read_end *read_end, struct aws_byte_buf *dst_buffer, size_t *num_bytes_read);
```
