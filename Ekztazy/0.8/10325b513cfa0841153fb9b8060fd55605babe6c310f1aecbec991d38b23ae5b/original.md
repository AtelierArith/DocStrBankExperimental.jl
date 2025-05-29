```
on_guild_role_update!(
    f::Function
    c::Client
)
```

Adds a handler for the GUILD_ROLE_UPDATE gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
