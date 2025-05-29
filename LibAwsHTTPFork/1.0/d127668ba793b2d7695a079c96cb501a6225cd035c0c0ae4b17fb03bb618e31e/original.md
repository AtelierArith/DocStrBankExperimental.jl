```
aws_websocket_release(websocket)
```

Decrement the websocket's ref-count. When the ref-count reaches zero, the connection will shut down, if it hasn't already. Users must release the websocket when they are done with it. The websocket's memory cannot be reclaimed until this is done. Callbacks may continue firing after this is called, with "shutdown" being the final callback. This function may be called from any thread.

It is safe to pass NULL, nothing will happen.

### Prototype

```c
void aws_websocket_release(struct aws_websocket *websocket);
```
