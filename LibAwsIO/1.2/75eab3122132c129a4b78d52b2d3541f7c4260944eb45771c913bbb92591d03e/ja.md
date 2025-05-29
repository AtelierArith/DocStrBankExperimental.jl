```
aws_message_pool_acquire(msg_pool, message_type, size_hint)
```

プールからメッセージを取得します。利用可能でない場合は、割り当てを試みます。メッセージが取得された場合、size_hintは単なるヒントであることに注意してください。戻り値の容量は実際のバッファサイズに設定されます。

### プロトタイプ

```c
struct aws_io_message *aws_message_pool_acquire( struct aws_message_pool *msg_pool, enum aws_io_message_type message_type, size_t size_hint);
```
