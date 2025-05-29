```
on_guild_role_delete!(
    f::Function
    c::Client
)
```

Adds a handler for the GUILD_ROLE_DELETE gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
