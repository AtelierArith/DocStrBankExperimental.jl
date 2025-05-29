```
aws_channel_handler_process_write_message(handler, slot, message)
```

ハンドラーのvtableでprocess*write*messageを呼び出します。

### プロトタイプ

```c
int aws_channel_handler_process_write_message( struct aws_channel_handler *handler, struct aws_channel_slot *slot, struct aws_io_message *message);
```
