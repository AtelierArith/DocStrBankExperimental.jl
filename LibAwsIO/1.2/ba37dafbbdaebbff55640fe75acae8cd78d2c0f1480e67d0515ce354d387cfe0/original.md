```
aws_channel_destroy(channel)
```

Mark the channel, along with all slots and handlers, for destruction. Must be called after shutdown has completed. Can be called from any thread assuming '[`aws_channel_shutdown`](@ref)()' has completed. Note that memory will not be freed until all users which acquired holds on the channel via [`aws_channel_acquire_hold`](@ref)(), release them via [`aws_channel_release_hold`](@ref)().

### Prototype

```c
void aws_channel_destroy(struct aws_channel *channel);
```
