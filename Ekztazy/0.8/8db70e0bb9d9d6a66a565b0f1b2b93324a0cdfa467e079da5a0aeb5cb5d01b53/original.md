```
on_guild_integrations_update!(
    f::Function
    c::Client
)
```

Adds a handler for the GUILD_INTEGRATIONS_UPDATE gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
