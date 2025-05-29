```
aws_websocket_close(websocket, free_scarce_resources_immediately)
```

Close the websocket connection. It is safe to call this, even if the connection is already closed or closing. The websocket will attempt to send a CLOSE frame during normal shutdown. If `free_scarce_resources_immediately` is true, the connection will be torn down as quickly as possible. This function may be called from any thread.

### Prototype

```c
void aws_websocket_close(struct aws_websocket *websocket, bool free_scarce_resources_immediately);
```
