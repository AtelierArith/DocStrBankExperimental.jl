```
aws_message_pool_init(msg_pool, alloc, args)
```

'msg_pool'をバックプールとして使用してメッセージプールを初期化し、'args'がコピーされます。

### プロトタイプ

```c
int aws_message_pool_init( struct aws_message_pool *msg_pool, struct aws_allocator *alloc, struct aws_message_pool_creation_args *args);
```
