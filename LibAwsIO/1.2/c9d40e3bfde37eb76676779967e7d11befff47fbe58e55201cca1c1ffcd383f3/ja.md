```
aws_channel_handler_process_read_message(handler, slot, message)
```

ハンドラーのvtableでprocess*read*messageを呼び出します

### プロトタイプ

```c
int aws_channel_handler_process_read_message( struct aws_channel_handler *handler, struct aws_channel_slot *slot, struct aws_io_message *message);
```
