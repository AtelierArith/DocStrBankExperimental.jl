```
on_message_create!(
    f::Function
    c::Client
)
```

Adds a handler for the MESSAGE_CREATE gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
