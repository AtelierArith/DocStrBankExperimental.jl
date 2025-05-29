```
on_channel_update!(
    f::Function
    c::Client
)
```

Adds a handler for the CHANNEL_UPDATE gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
