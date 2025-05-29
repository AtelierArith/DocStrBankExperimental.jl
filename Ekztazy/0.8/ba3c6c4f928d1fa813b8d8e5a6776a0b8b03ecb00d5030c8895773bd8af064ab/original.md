```
heartbeat_ping(c::Client) -> Nullable{Period}
```

Get the [`Client`](@ref)'s ping time to the gateway. If the client is not connected, or no heartbeats have been sent/acknowledged, `nothing` is returned.
