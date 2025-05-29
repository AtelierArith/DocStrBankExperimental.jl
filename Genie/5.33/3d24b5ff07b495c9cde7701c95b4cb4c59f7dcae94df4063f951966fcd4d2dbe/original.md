```
up(port::Int = Genie.config.server_port, host::String = Genie.config.server_host;
    ws_port::Int = Genie.config.websockets_port, async::Bool = ! Genie.config.run_as_server) :: Nothing
```

Starts the web server. Alias for `Server.up`

# Arguments

  * `port::Int`: the port used by the web server
  * `host::String`: the host used by the web server
  * `ws_port::Int`: the port used by the Web Sockets server
  * `async::Bool`: run the web server task asynchronously

# Examples

```julia-repl
julia> up(8000, "127.0.0.1", async = false)
[ Info: Ready!
Web Server starting at http://127.0.0.1:8000
```
