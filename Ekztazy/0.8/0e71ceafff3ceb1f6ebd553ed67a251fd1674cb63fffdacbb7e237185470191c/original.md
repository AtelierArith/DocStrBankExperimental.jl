```
on_guild_role_create!(
    f::Function
    c::Client
)
```

Adds a handler for the GUILD_ROLE_CREATE gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
