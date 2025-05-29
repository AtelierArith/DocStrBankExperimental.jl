```
aws_channel_slot_set_handler(slot, handler)
```

スロットのハンドラーを設定します。スロットはまた、get*current*window_size()を呼び出し、ウィンドウの更新を上流に伝播させます。

### プロトタイプ

```c
int aws_channel_slot_set_handler(struct aws_channel_slot *slot, struct aws_channel_handler *handler);
```
