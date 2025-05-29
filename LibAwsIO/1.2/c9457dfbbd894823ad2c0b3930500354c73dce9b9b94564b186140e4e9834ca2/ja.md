```
aws_pipe_clean_up_read_end(read_end)
```

パイプの読み取りエンドをクリーンアップします。これは、接続されたイベントループのスレッドで呼び出す必要があります。

### プロトタイプ

```c
int aws_pipe_clean_up_read_end(struct aws_pipe_read_end *read_end);
```
