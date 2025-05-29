```
aws_channel_shutdown(channel, error_code)
```

Initiates shutdown of the channel. Shutdown will begin with the left-most slot. Each handler will invoke '[`aws_channel_slot_on_handler_shutdown_complete`](@ref)' once they've finished their shutdown process for the read direction. Once the right-most slot has shutdown in the read direction, the process will start shutting down starting on the right-most slot. Once the left-most slot has shutdown in the write direction, 'callbacks->shutdown_completed' will be invoked in the event loop's thread.

This function can be called from any thread.

### Prototype

```c
int aws_channel_shutdown(struct aws_channel *channel, int error_code);
```
