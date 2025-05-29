```
aws_http2_connection_update_window(http2_connection, increment_size)
```

Increment the connection's flow-control window to keep data flowing (HTTP/2 only).

If the connection was created with `conn_manual_window_management` set true, the flow-control window of the connection will shrink as body data is received for all the streams created on it. (headers, padding, and other metadata do not affect the window). The initial connection flow-control window is 65,535. Once the connection's flow-control window reaches to 0, all the streams on the connection stop receiving any further data.

If `conn_manual_window_management` is false, this call will have no effect. The connection maintains its flow-control windows such that no back-pressure is applied and data arrives as fast as possible.

If you are not connected, this call will have no effect.

Crashes when the connection is not http2 connection. The limit of the Maximum Size is 2**31 - 1. And client will make sure the WINDOW_UPDATE frame to be valid.

The client control exactly when the WINDOW_UPDATE frame sent. Check `conn_window_size_threshold_to_send_update` for details.

# Arguments

  * `http2_connection`: HTTP/2 connection.
  * `increment_size`: The size to increment for the connection's flow control window

### Prototype

```c
void aws_http2_connection_update_window(struct aws_http_connection *http2_connection, uint32_t increment_size);
```
