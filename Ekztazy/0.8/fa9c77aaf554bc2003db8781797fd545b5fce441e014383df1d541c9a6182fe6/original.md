```
on_guild_create!(
    f::Function
    c::Client
)
```

Adds a handler for the GUILD_CREATE gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
