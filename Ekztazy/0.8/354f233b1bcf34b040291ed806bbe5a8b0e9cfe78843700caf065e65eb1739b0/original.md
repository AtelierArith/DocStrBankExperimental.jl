```
on_user_update!(
    f::Function
    c::Client
)
```

Adds a handler for the USER_UPDATE gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
