```
on_channel_pins_update!(
    f::Function
    c::Client
)
```

Adds a handler for the CHANNEL_PINS_UPDATE gateway event. The `f` parameter's signature should be:

```
    (ctx::Context) -> Any 
```
