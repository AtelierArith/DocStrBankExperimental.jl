```
kerbal_connect(f::Function, client_name::String, host::String="localhost", port::Int64=50000, stream_port::Int64=50001)
```

Do-notation version of `kerbal_connect`, automatically closing the connection after termination of the do block.

# Examples

Connect to localhost as "test" and using the default ports:

```julia-repl
julia> kerbal_connect("test") do conn
         println("connected!")
       end
```
