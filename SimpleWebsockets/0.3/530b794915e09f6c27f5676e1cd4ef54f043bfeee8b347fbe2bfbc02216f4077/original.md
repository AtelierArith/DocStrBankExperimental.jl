```
emit(server::WebsocketServer, data::Union{Array{UInt8,1}, String, Number})
```

Sends the given `data` as a message to all clients connected to the server.

# Example

```julia
emit(server, "Hello everybody from your loving server.")
```
