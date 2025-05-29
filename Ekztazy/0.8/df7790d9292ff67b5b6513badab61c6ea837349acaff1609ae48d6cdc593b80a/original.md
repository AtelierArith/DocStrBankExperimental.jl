```
on_voice_server_update!(
    f::Function
    c::Client
)
```

Adds a handler for the VOICE_SERVER_UPDATE gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
