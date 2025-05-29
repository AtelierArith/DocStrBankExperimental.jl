```
on_guild_delete!(
    f::Function
    c::Client
)
```

Adds a handler for the GUILD_DELETE gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
