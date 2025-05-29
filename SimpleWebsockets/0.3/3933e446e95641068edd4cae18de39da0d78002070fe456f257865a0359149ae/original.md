```
listen(callback::Function, server::WebsocketServer, event::Symbol)
```

Register event callbacks onto a server. The callback must be a function with exactly one argument.

Valid events are:

  * :listening
  * :client
  * :connectError
  * :peerError
  * :closed

# Example

```julia
listen(server, :client) do client
    #...
end
```
