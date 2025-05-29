```
aws_channel_slot_on_handler_shutdown_complete(slot, dir, err_code, free_scarce_resources_immediately)
```

ハンドラーが 'dir' 方向でのシャットダウンを完了した後に呼び出されます。シャットダウンプロセスをチャネル内の次のハンドラーに伝播させます。

### プロトタイプ

```c
int aws_channel_slot_on_handler_shutdown_complete( struct aws_channel_slot *slot, enum aws_channel_direction dir, int err_code, bool free_scarce_resources_immediately);
```
