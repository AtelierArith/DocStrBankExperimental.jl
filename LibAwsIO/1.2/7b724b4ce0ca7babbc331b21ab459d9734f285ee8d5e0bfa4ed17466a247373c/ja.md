```
aws_pipe_init(read_end, read_end_event_loop, write_end, write_end_event_loop, allocator)
```

OS固有の双方向パイプを開きます。読み取り方向はread*endに格納されます。書き込み方向はwrite*endに格納されます。各端はイベントループに接続されている必要があり、各端へのさらなる呼び出しはそのイベントループのスレッド上で行う必要があります。

### プロトタイプ

```c
int aws_pipe_init( struct aws_pipe_read_end *read_end, struct aws_event_loop *read_end_event_loop, struct aws_pipe_write_end *write_end, struct aws_event_loop *write_end_event_loop, struct aws_allocator *allocator);
```
