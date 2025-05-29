```
aws_websocket_acquire(websocket)
```

Increment the websocket's ref-count, preventing it from being destroyed.

# Returns

Always returns the same pointer that is passed in.

### Prototype

```c
struct aws_websocket *aws_websocket_acquire(struct aws_websocket *websocket);
```
