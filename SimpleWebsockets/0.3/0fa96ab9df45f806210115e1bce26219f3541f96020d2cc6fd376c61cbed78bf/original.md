```
serve(server::WebsocketServer, [port::Int, host::String; options...])
```

Opens up a TCP connection listener. Blocks while the server is listening.

Defaults:

  * port: 8080
  * host: "localhost"

`; options...` are passed to the underlying [HTTP.servers.listen](https://juliaweb.github.io/HTTP.jl/v1.0.2/server/#HTTP.listen)

# Example

```julia
closed = Condition()
#...
@async serve(server, 8081, "localhost")
#...
wait(closed)
```
