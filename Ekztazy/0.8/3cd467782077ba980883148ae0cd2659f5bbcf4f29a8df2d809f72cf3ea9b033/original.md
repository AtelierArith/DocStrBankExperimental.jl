```
on_voice_state_update!(
    f::Function
    c::Client
)
```

Adds a handler for the VOICE_STATE_UPDATE gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
