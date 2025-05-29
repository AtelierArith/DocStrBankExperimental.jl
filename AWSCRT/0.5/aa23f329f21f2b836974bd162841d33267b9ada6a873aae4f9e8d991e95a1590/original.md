```
on_message(connection::MQTTConnection, callback::Union{OnMessage,Nothing})
```

Set callback to be invoked when ANY message is received.

Arguments:

  * `connection (MQTTConnection)`: Connection to use.
  * `callback (Union{OnMessage,Nothing})`: Optional callback invoked when message received. See [`OnMessage`](@ref) for the required signature. Set to `nothing` to clear this callback.

Returns nothing.

!!! note
    All callbacks are run concurrently. Your callback implementations must be thread-safe. There is no concurrency limit.

