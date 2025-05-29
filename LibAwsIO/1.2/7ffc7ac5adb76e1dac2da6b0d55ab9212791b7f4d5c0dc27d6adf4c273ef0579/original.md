```
testing_channel_push_read_str(channel, str)
```

Create an [`aws_io_message`](@ref), containing the following data, and pushes it up the channel in the read direction

### Prototype

```c
static inline int testing_channel_push_read_str(struct testing_channel *channel, const char *str);
```
