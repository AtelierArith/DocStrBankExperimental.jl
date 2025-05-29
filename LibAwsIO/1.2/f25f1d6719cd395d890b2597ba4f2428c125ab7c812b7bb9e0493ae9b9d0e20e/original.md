```
testing_channel_push_write_message(testing, message)
```

when you want to test the write path of your handler, call this with the message you want it to write. A downstream handler must have been installed

### Prototype

```c
static inline int testing_channel_push_write_message(struct testing_channel *testing, struct aws_io_message *message);
```
