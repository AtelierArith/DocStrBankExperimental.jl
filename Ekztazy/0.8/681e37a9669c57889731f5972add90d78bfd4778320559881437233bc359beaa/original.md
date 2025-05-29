```
on_guild_ban_add!(
    f::Function
    c::Client
)
```

Adds a handler for the GUILD_BAN_ADD gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
