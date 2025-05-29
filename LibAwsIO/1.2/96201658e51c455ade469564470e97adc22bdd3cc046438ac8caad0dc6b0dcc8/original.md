```
aws_channel_acquire_message_from_pool(channel, message_type, size_hint)
```

Acquires a message from the event loop's message pool. size_hint is merely a hint, it may be smaller than you requested and you are responsible for checking the bounds of it. If the returned message is not large enough, you must send multiple messages. This cannot fail, it never returns NULL.

### Prototype

```c
struct aws_io_message *aws_channel_acquire_message_from_pool( struct aws_channel *channel, enum aws_io_message_type message_type, size_t size_hint);
```
