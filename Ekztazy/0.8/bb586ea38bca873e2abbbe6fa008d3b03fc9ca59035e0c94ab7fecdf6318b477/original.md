```
on_channel_delete!(
    f::Function
    c::Client
)
```

Adds a handler for the CHANNEL_DELETE gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
