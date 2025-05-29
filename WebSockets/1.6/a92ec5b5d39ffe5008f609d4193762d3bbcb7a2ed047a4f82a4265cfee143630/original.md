`writeguarded(websocket, message) => Bool`

Return true if write is successful, false if not. The peer can potentially disconnect at any time, but no matter the cause you will usually just want to exit your websocket handling function when you can't write to it.

To check the errors (if you get any), temporarily set loging min_level to Logging.debug, e.g:

```julia
using WebSockets, Logging
global_logger(WebSocketLogger(stderr, Logging.Debug));
```
