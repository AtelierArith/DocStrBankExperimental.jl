```
testing_channel_push_read_str_ignore_errors(channel, str)
```

Create an [`aws_io_message`](@ref), containing the following data. Tries to push it up the channel in the read direction, but don't assert if the message can't be sent. Useful for testing data that arrives during handler shutdown

### Prototype

```c
static inline int testing_channel_push_read_str_ignore_errors(struct testing_channel *channel, const char *str);
```
