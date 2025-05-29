```
on_message_delete_bulk!(
    f::Function
    c::Client
)
```

Adds a handler for the MESSAGE_DELETE_BULK gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
