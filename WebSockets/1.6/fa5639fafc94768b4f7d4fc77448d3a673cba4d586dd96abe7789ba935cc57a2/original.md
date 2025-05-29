```
read(ws::WebSocket)
```

Typical use:     msg = String(read(ws)) Read one non-control message from a WebSocket. Any control messages that are read will be handled by the handle*control*frame function. Only the data (contents/body/payload) of the message will be returned as a Vector{UInt8}.

This function will not return until a full non-control message has been read.
