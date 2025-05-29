```
aws_channel_slot_insert_end(channel, to_add)
```

チャネルの末尾に'to*add'を挿入します。最初の[`aws*channel*slot*new`](@ref)()の呼び出しは、それをチャネルに暗黙的に追加することに注意してください。

### プロトタイプ

```c
int aws_channel_slot_insert_end(struct aws_channel *channel, struct aws_channel_slot *to_add);
```
