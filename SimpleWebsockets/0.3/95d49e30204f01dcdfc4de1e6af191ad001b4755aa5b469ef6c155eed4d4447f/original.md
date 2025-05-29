```
listen(callback::Function, ws::SimpleWebsockets.WebsocketConnection, event::Symbol)
```

Register event callbacks onto a `WebsocketConnection`. The callback must be a function with exactly one argument.

Valid events are:

  * :message
  * :pong
  * :error
  * :close

# Example

```julia
listen(ws::WebsocketConnection, :message) do message
    #...
end
```
