```
aws_channel_slot_insert_left(slot, to_add)
```

は、'to*add'をslotのすぐ左の位置に挿入します。最初の[`aws*channel*slot*new`](@ref)()の呼び出しは、チャネルに暗黙的に追加されることに注意してください。

### プロトタイプ

```c
int aws_channel_slot_insert_left(struct aws_channel_slot *slot, struct aws_channel_slot *to_add);
```
