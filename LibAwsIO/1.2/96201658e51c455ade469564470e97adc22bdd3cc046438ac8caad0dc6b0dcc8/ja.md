```
aws_channel_acquire_message_from_pool(channel, message_type, size_hint)
```

イベントループのメッセージプールからメッセージを取得します。size_hintは単なるヒントであり、要求したサイズよりも小さい場合がありますので、その範囲を確認する責任があります。返されたメッセージが十分に大きくない場合は、複数のメッセージを送信する必要があります。これは失敗することはなく、NULLを返すことはありません。

### プロトタイプ

```c
struct aws_io_message *aws_channel_acquire_message_from_pool( struct aws_channel *channel, enum aws_io_message_type message_type, size_t size_hint);
```
