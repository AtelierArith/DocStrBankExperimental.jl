```
on_guild_ban_remove!(
    f::Function
    c::Client
)
```

Adds a handler for the GUILD_BAN_REMOVE gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
