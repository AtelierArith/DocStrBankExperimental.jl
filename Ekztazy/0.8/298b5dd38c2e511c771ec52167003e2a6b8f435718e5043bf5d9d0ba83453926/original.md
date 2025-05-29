```
on_message_reaction_remove!(
    f::Function
    c::Client
)
```

Adds a handler for the MESSAGE_REACTION_REMOVE gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
