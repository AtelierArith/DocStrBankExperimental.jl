```
aws_pipe_clean_up_write_end(write_end)
```

パイプの書き込みエンドをクリーンアップします。これは、接続されたイベントループのスレッドで呼び出す必要があります。

### プロトタイプ

```c
int aws_pipe_clean_up_write_end(struct aws_pipe_write_end *write_end);
```
