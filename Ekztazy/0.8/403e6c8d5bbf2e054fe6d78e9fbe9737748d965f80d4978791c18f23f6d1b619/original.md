```
on_guild_emojis_update!(
    f::Function
    c::Client
)
```

Adds a handler for the GUILD_EMOJIS_UPDATE gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
