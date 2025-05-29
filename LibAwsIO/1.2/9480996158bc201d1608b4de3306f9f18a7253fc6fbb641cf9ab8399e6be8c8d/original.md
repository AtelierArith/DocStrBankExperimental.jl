```
aws_message_pool_release(msg_pool, message)
```

Releases message to the pool if space is available, otherwise frees `message`

# Arguments

  * `message`:

### Prototype

```c
void aws_message_pool_release(struct aws_message_pool *msg_pool, struct aws_io_message *message);
```
