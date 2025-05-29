```
aws_http2_connection_get_remote_settings(http2_connection, out_settings)
```

Get the settings received from remote peer, which we are using to restricts the message to send.

# Arguments

  * `http2_connection`: HTTP/2 connection.
  * `out_settings`: fixed size array of [`aws_http2_setting`](@ref) gets set to the remote settings

### Prototype

```c
void aws_http2_connection_get_remote_settings( const struct aws_http_connection *http2_connection, struct aws_http2_setting out_settings[AWS_HTTP2_SETTINGS_COUNT]);
```
