```
kerbal_connect(client_name::String, host::String="localhost", port::Int64=50000, stream_port::Int64=50001)
```

Connect to `host` at port `port` (with stream port `stream_port`) and with the displayed name `client_name`. Default values are set up for the default localhost configuration. 

# Examples

Connect to localhost as "test" and using the default ports:

```julia-repl
julia> conn = kerbal_connect("test")
```

Connect to localhost using ports 9001/9002:

```julia-repl
julia> conn = kerbal_connect("test", "localhost", 9001, 9002)
```

Connect to a server at the IP address 192.168.1.1, and ports 9001/9002:

```julia-repl
julia> conn = kerbal_connect("test", "192.168.1.1", 9001, 9002)
```
