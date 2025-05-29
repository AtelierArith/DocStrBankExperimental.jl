```
aws_message_pool_release(msg_pool, message)
```

メッセージをプールに解放します。スペースが利用可能な場合はプールに解放し、そうでない場合は `message` を解放します。

# 引数

  * `message`:

### プロトタイプ

```c
void aws_message_pool_release(struct aws_message_pool *msg_pool, struct aws_io_message *message);
```
