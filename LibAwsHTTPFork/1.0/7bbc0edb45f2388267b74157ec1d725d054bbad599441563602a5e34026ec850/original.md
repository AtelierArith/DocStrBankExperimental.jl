```
aws_http_stream_update_window(stream, increment_size)
```

Increment the stream's flow-control window to keep data flowing.

If the connection was created with `manual_window_management` set true, the flow-control window of each stream will shrink as body data is received (headers, padding, and other metadata do not affect the window). The connection's `initial_window_size` determines the starting size of each stream's window. If a stream's flow-control window reaches 0, no further data will be received.

If `manual_window_management` is false, this call will have no effect. The connection maintains its flow-control windows such that no back-pressure is applied and data arrives as fast as possible.

For HTTP/2, the client control exactly when the WINDOW_UPDATE frame sent. And client will make sure the WINDOW_UPDATE frame to be valid. Check `stream_window_size_threshold_to_send_update` for details.

### Prototype

```c
void aws_http_stream_update_window(struct aws_http_stream *stream, size_t increment_size);
```
