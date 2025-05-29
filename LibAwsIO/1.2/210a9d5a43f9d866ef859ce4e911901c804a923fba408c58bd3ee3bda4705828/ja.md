```
aws_channel_slot_insert_right(slot, to_add)
```

は 'to*add' を slot のすぐ右の位置に挿入します。最初の [`aws*channel*slot*new`](@ref)() の呼び出しは、チャネルに暗黙的に追加されることに注意してください。

### プロトタイプ

```c
int aws_channel_slot_insert_right(struct aws_channel_slot *slot, struct aws_channel_slot *to_add);
```
