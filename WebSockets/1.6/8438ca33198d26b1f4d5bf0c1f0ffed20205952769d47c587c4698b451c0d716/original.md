```
close(ws::WebSocket)
close(ws::WebSocket, statusnumber = n)
close(ws::WebSocket, statusnumber = n, freereason = "my reason")
```

Send an OPCODE_CLOSE frame, and wait for the same response or until a reasonable amount of time, 10.0 s, has passed. Data received while closing is dropped. Status number n according to RFC 6455 7.4.1 can be included, see WebSockets.codeDesc
