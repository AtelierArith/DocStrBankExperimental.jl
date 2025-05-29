```
aws_channel_slot_acquire_max_message_for_write(slot)
```

書き込み方向に送信できる最大の合理的なデータメッセージを要求する[`aws_channel_acquire_message_from_pool`](@ref)()を呼び出す便利な関数で、上流のオーバーヘッドが考慮されています。これは失敗することはなく、NULLを返すことはありません。

### プロトタイプ

```c
struct aws_io_message *aws_channel_slot_acquire_max_message_for_write(struct aws_channel_slot *slot);
```
