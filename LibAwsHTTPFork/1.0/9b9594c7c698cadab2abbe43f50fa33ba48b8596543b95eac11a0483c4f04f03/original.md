```
aws_http2_connection_change_settings(http2_connection, settings_array, num_settings, on_completed, user_data)
```

Send a SETTINGS frame (HTTP/2 only). SETTINGS will be applied locally when SETTINGS ACK is received from peer.

# Arguments

  * `http2_connection`: HTTP/2 connection.
  * `settings_array`: The array of settings to change. Note: each setting has its boundary.
  * `num_settings`: The num of settings to change in settings_array.
  * `on_completed`: Optional callback, see [`aws_http2_on_change_settings_complete_fn`](@ref).
  * `user_data`: User-data pass to on_completed callback.

### Prototype

```c
int aws_http2_connection_change_settings( struct aws_http_connection *http2_connection, const struct aws_http2_setting *settings_array, size_t num_settings, aws_http2_on_change_settings_complete_fn *on_completed, void *user_data);
```
