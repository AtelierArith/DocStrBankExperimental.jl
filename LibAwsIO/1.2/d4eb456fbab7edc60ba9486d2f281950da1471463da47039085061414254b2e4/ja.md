```
aws_channel_slot_replace(remove, new_slot)
```

removeをnew_slotで置き換えます。removeとそのハンドラーのメモリを解放します。

### プロトタイプ

```c
int aws_channel_slot_replace(struct aws_channel_slot *remove, struct aws_channel_slot *new_slot);
```
