```
on_resumed!(
    f::Function
    c::Client
)
```

Adds a handler for the RESUMED gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
