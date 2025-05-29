```
aws_channel_slot_shutdown(slot, dir, err_code, free_scarce_resources_immediately)
```

スロットのシャットダウンを開始します。コールバックの callbacks->on*shutdown*completed は、シャットダウンプロセスが完了すると呼び出されます。

### プロトタイプ

```c
int aws_channel_slot_shutdown( struct aws_channel_slot *slot, enum aws_channel_direction dir, int err_code, bool free_scarce_resources_immediately);
```
