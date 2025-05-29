```
aws_http2_connection_get_local_settings(http2_connection, out_settings)
```

Get the local settings we are using to affect the decoding.

# Arguments

  * `http2_connection`: HTTP/2 connection.
  * `out_settings`: fixed size array of [`aws_http2_setting`](@ref) gets set to the local settings

### Prototype

```c
void aws_http2_connection_get_local_settings( const struct aws_http_connection *http2_connection, struct aws_http2_setting out_settings[AWS_HTTP2_SETTINGS_COUNT]);
```
