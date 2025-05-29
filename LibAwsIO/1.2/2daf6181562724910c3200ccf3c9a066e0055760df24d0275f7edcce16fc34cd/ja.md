```
aws_pipe_unsubscribe_from_readable_events(read_end)
```

パイプの読み取りエンドでのイベントに関する通知の受信を停止します。これは、接続されたイベントループのスレッドで呼び出す必要があります。

### プロトタイプ

```c
int aws_pipe_unsubscribe_from_readable_events(struct aws_pipe_read_end *read_end);
```
