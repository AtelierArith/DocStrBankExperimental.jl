```
WebSockets
```

This module implements the WebSockets protocol. It relies on the package HTTP.jl.

Websocket|server relies on a client initiating the connection. Websocket|client initiate the connection.

The client side of the connection is most typically a browser with scripts enabled. Browsers are always the initiating, client side. But the peer can be any program, in any language, that follows the protocol. That includes another Julia session, running in a parallel process or task.

```
Future improvements:
```

1. Check rsv1 to rsv3 values. This will reduce bandwidth.
2. Optimize maskswitch!, possibly threaded above a certain limit.
3. Split messages over several frames.
