```
testing_channel_push_read_data(channel, data)
```

Create an [`aws_io_message`](@ref), containing the following data, and pushes it up the channel in the read direction

### Prototype

```c
static inline int testing_channel_push_read_data(struct testing_channel *channel, struct aws_byte_cursor data);
```
