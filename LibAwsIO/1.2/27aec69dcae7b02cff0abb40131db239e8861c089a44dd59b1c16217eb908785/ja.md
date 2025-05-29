```
aws_pipe_get_read_end_event_loop(read_end)
```

パイプの読み取り端に接続されたイベントループを取得します。これは任意のスレッドで呼び出すことができます。

### プロトタイプ

```c
struct aws_event_loop *aws_pipe_get_read_end_event_loop(const struct aws_pipe_read_end *read_end);
```
