```
aws_pipe_write(write_end, src_buffer, on_completed, user_data)
```

ソースバッファからパイプへの非同期書き込みを開始します。`src_buffer`によって参照されるデータは、操作が完了するまでメモリに残っている必要があります。操作が完了または失敗したときに、`on_complete`がイベントループスレッドで呼び出されます。コールバックのパイプ引数は、パイプがクリーンアップされた後にコールバックが呼び出された場合、NULLになります。これは、接続されたイベントループのスレッドで呼び出す必要があります。

### プロトタイプ

```c
int aws_pipe_write( struct aws_pipe_write_end *write_end, struct aws_byte_cursor src_buffer, aws_pipe_on_write_completed_fn *on_completed, void *user_data);
```
