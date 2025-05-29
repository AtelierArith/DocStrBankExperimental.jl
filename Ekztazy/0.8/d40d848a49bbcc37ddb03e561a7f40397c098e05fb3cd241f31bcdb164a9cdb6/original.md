```
on_guild_member_add!(
    f::Function
    c::Client
)
```

Adds a handler for the GUILD_MEMBER_ADD gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
