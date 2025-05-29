```
on_message_delete!(
    f::Function
    c::Client
)
```

Adds a handler for the MESSAGE_DELETE gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
