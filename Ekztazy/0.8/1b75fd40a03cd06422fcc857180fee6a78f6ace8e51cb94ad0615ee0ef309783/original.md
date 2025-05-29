```
on_typing_start!(
    f::Function
    c::Client
)
```

Adds a handler for the TYPING_START gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
