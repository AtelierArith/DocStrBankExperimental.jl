```
on_ready!(
    f::Function
    c::Client
)
```

Adds a handler for the READY gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
