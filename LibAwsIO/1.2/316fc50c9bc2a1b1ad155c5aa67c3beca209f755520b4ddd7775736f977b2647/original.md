```
testing_channel_push_read_message(testing, message)
```

when you want to test the read path of your handler, call this with the message you want it to read.

### Prototype

```c
static inline int testing_channel_push_read_message(struct testing_channel *testing, struct aws_io_message *message);
```
