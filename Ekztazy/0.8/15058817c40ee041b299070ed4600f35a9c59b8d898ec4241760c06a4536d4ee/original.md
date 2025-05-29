```
on_message_reaction_remove_all!(
    f::Function
    c::Client
)
```

Adds a handler for the MESSAGE_REACTION_REMOVE_ALL gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
