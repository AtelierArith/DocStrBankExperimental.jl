```
aws_websocket_upgrade(allocator, stream, options)
```

Upgrade an incoming HTTP connection to a websocket connection. This function should be called from the on_request_done callback of a request handler. It expects a fully constructed request and will handle sending the handshake response and install the websocket handler into the channel.

### Prototype

```c
struct aws_websocket *aws_websocket_upgrade( struct aws_allocator *allocator, struct aws_http_stream *stream, const struct aws_websocket_server_upgrade_options *options);
```
