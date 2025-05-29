```
on_guild_members_chunk!(
    f::Function
    c::Client
)
```

Adds a handler for the GUILD_MEMBERS_CHUNK gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
