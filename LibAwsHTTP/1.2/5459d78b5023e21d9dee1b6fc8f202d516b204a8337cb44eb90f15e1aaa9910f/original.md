```
aws_websocket_convert_to_midchannel_handler(websocket)
```

Convert the websocket into a mid-channel handler. The websocket will stop being usable via its public API and become just another handler in the channel. The caller will likely install a channel handler to the right. This must not be called in the middle of an incoming frame (between "frame begin" and "frame complete" callbacks). This MUST be called from the websocket's thread.

If successful: - Other than [`aws_websocket_release`](@ref)(), all calls to aws_websocket_x() functions are ignored. - The websocket will no longer invoke any "incoming frame" callbacks. - aws_io_messages written by a downstream handler will be wrapped in binary data frames and sent upstream. The data may be split/combined as it is sent along. - aws_io_messages read from upstream handlers will be scanned for binary data frames. The payloads of these frames will be sent downstream. The payloads may be split/combined as they are sent along. - An incoming close frame will automatically result in channel-shutdown. - [`aws_websocket_release`](@ref)() must still be called or the websocket and its channel will never be cleaned up. - The websocket will still invoke its "on connection shutdown" callback when channel shutdown completes.

If unsuccessful, NULL is returned and the websocket is unchanged.

### Prototype

```c
int aws_websocket_convert_to_midchannel_handler(struct aws_websocket *websocket);
```
