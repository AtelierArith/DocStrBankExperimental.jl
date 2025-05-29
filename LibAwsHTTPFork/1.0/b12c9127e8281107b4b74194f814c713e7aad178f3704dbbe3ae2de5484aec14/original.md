```
aws_websocket_client_connect(options)
```

Asynchronously establish a client websocket connection. The on_connection_setup callback is invoked when the operation has finished creating a connection, or failed.

### Prototype

```c
int aws_websocket_client_connect(const struct aws_websocket_client_connection_options *options);
```
