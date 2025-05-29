```
aws_channel_release_hold(channel)
```

Release a hold on the channel's memory, allowing it to be freed. This may be called before or after [`aws_channel_destroy`](@ref)().

### Prototype

```c
void aws_channel_release_hold(struct aws_channel *channel);
```
