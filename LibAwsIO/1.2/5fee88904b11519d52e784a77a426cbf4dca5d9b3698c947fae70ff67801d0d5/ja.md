```
aws_channel_slot_new(channel)
```

チャンネルで使用するための新しいスロットを割り当てて初期化します。これがチャンネル内の最初のスロットである場合、自動的にチャンネルに最初のスロットとして追加されます。特定のチャンネルに対するその後のすべての呼び出しでは、スロットは[`aws_channel_slot_insert_right`](@ref)()、[`aws_channel_slot_insert_end`](@ref)()、および[`aws_channel_slot_insert_left`](@ref)() APIを介してチャンネルに追加する必要があります。

### プロトタイプ

```c
struct aws_channel_slot *aws_channel_slot_new(struct aws_channel *channel);
```
