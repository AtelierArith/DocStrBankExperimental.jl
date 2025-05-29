```
aws_websocket_increment_read_window(websocket, size)
```

Manually increment the read window to keep frames flowing.

If the websocket was created with `manual_window_management` set true, then whenever the read window reaches 0 you will stop receiving data. The websocket's `initial_window_size` determines the starting size of the read window. The read window shrinks as you receive the payload from "data" frames (TEXT, BINARY, and CONTINUATION). Use [`aws_websocket_increment_read_window`](@ref)() to increment the window again and keep frames flowing. Maintain a larger window to keep up high throughput. You only need to worry about the payload from "data" frames. The websocket automatically increments the window to account for any other incoming bytes, including other parts of a frame (opcode, payload-length, etc) and the payload of other frame types (PING, PONG, CLOSE).

If the websocket was created with `manual_window_management` set false, this function does nothing.

This function may be called from any thread.

### Prototype

```c
void aws_websocket_increment_read_window(struct aws_websocket *websocket, size_t size);
```
