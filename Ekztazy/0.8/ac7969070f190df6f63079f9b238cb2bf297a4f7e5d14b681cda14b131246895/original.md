```
on_message_reaction_add!(
    f::Function
    c::Client
)
```

Adds a handler for the MESSAGE_REACTION_ADD gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
