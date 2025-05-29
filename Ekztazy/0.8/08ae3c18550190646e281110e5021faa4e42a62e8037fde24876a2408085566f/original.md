```
component!(
    f::Function
    c::Client
    custom_id::AbstractString
    kwargs...
)
```

Adds a handler for INTERACTION CREATE gateway events where the InteractionData's `custom_id` field matches `custom_id`. The `f` parameter signature should be:

```
(ctx::Context) -> Any 
```
