```
aws_channel_slot_upstream_message_overhead(slot)
```

現在の上流ハンドラーのオーバーヘッドを取得します。これは、断片化を避けるためのヒントを提供します。

### プロトタイプ

```c
size_t aws_channel_slot_upstream_message_overhead(struct aws_channel_slot *slot);
```
