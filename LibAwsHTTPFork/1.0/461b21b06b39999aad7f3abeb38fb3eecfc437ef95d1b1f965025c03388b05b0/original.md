```
aws_http_proxy_new_socket_channel(channel_options, proxy_options)
```

Establish an arbitrary protocol connection through an http proxy via tunneling CONNECT. Alpn is not required for this connection process to succeed, but we encourage its use if available.

# Arguments

  * `channel_options`: configuration options for the socket level connection
  * `proxy_options`: configuration options for the proxy connection

# Returns

AWS_OP_SUCCESS if the asynchronous channel kickoff succeeded, AWS_OP_ERR otherwise

### Prototype

```c
int aws_http_proxy_new_socket_channel( struct aws_socket_channel_bootstrap_options *channel_options, const struct aws_http_proxy_options *proxy_options);
```
