```
WebSockets.serve(server::ServerWS, port)
WebSockets.serve(server::ServerWS, host, port)
WebSockets.serve(server::ServerWS, host, port, verbose)
```

A higher level interface for WebSockets.HTTP.listen. If you are running serve asyncronously, the serve task will exit when you close(ServerWS).

Puts any caught error and stacktrace on the server.out channel. The server.in channel is used by close(ServerWS).

# Example

```julia
    @async WebSockets.serve(myserver_WS, "127.0.0.1", 8080)
```

After a suspected connection task failure:

```julia
    if isready(myserver_WS.out)
        stack_trace = take!(myserver_WS.out)
    end
```
