```
aws_channel_slot_increment_read_window(slot, window)
```

上流（左側）にウィンドウ更新通知を発行します。

### プロトタイプ

```c
int aws_channel_slot_increment_read_window(struct aws_channel_slot *slot, size_t window);
```
