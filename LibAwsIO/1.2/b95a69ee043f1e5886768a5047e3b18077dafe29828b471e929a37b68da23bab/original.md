```
aws_channel_set_statistics_handler(channel, handler)
```

Instrument a channel with a statistics handler. While instrumented with a statistics handler, the channel will periodically report per-channel-handler-specific statistics about handler performance and state.

Assigning a statistics handler to a channel is a transfer of ownership – the channel will clean up the handler appropriately. Statistics handlers may be changed dynamically (for example, the upgrade from a vanilla http channel to a websocket channel), but this function may only be called from the event loop thread that the channel is a part of.

The first possible hook to set a statistics handler is the channel's creation callback.

### Prototype

```c
int aws_channel_set_statistics_handler(struct aws_channel *channel, struct aws_crt_statistics_handler *handler);
```
