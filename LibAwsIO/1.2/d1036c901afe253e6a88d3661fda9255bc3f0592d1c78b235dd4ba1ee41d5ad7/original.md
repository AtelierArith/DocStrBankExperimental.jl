```
aws_channel_acquire_hold(channel)
```

Prevent a channel's memory from being freed. Any number of users may acquire a hold to prevent a channel and its handlers from being unexpectedly freed. Any user which acquires a hold must release it via [`aws_channel_release_hold`](@ref)(). Memory will be freed once all holds are released and [`aws_channel_destroy`](@ref)() has been called.

### Prototype

```c
void aws_channel_acquire_hold(struct aws_channel *channel);
```
