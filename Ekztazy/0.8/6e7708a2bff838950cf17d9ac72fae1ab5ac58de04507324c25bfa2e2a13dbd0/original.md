```
on_guild_member_remove!(
    f::Function
    c::Client
)
```

Adds a handler for the GUILD_MEMBER_REMOVE gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
