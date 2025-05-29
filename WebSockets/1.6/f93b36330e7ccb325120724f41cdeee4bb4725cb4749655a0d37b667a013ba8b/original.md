`readguarded(websocket) => (Vector, Bool)`

Return (data::Vector, true)         or         (Vector{UInt8}(), false)

The peer can potentially disconnect at any time, but no matter the cause you will usually just want to exit your websocket handling function when you can't write to it.

E.g.

```julia
while true
    data, success = readguarded(websocket)
    !success && break
    println(String(data))
end
```

To check the errors (if you get any), temporarily set loging min_level to Logging.debug, e.g:

```julia
using WebSockets, Logging
global_logger(WebSocketLogger(stderr, Logging.Debug));
```
