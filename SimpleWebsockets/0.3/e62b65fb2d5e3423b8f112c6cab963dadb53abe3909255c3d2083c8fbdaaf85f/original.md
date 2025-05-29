```
listen(callback::Function, client::SimpleWebsockets.WebsocketClient, event::Symbol)
```

Register event callbacks onto a client. The callback must be a function with exactly one argument.

Valid events are:

  * :connect
  * :connectError

# Example

```julia
listen(client, :connect) do ws
    #...
end
```
