```
on_guild_update!(
    f::Function
    c::Client
)
```

Adds a handler for the GUILD_UPDATE gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
