```
serve_repl([address=Sockets.localhost,] port=27754; [on_client_connect=nothing])
serve_repl(server)
```

Start a REPL server listening on interface `address` and `port`. In normal operation `serve_repl()` serves REPL clients indefinitely (ie., it does not return), so you will generally want to launch it using `@async serve_repl()` to do other useful work at the same time.

The hook `on_client_connect` may be supplied to modify the `ServerSideSession` for a client after each client connects. This can be used to define the default module in which the client evaluates commands.

If you want to be able to stop the server you can pass an already-listening `server` object (the result of `Sockets.listen()`). The server can then be cancelled from another task using `close(server)` as necessary to control the server lifetime.

## Security

`serve_repl()` uses an *unauthenticated, unecrypted protocol* so it should not be used on open networks or multi-user machines where other users aren't trusted. For open networks, use the default `address=Sockets.localhost` and the automatic ssh tunnel support provided by the client-side `connect_repl()`.
