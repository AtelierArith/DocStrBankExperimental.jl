```
aws_pipe_get_write_end_event_loop(write_end)
```

パイプの書き込み端に接続されたイベントループを取得します。これは任意のスレッドで呼び出すことができます。

### プロトタイプ

```c
struct aws_event_loop *aws_pipe_get_write_end_event_loop(const struct aws_pipe_write_end *write_end);
```
