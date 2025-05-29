```
aws_websocket_send_frame(websocket, options)
```

Send a websocket frame. The `options` struct is copied. A callback will be invoked when the operation completes. This function may be called from any thread.

### Prototype

```c
int aws_websocket_send_frame(struct aws_websocket *websocket, const struct aws_websocket_send_frame_options *options);
```
