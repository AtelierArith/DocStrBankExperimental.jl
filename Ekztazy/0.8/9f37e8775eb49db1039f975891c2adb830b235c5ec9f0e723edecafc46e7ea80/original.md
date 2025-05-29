```
start(c::Client)
```

Creates a handler to generate [`ApplicationCommand`](@ref)s.

Creates handlers for GuildCreate events.

Calls `open` then `wait` on the [`Client`](@ref).
