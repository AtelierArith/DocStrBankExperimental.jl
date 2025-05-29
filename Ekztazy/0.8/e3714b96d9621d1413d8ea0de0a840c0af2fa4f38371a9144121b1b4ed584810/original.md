```
select!(
    f::Function
    c::Client
    custom_id::AbstractString
    args::Vector{Tuple}
    kwargs...
)
```

Adds a handler for INTERACTION CREATE gateway events where the InteractionData's `custom_id` field matches `custom_id`. The `f` parameter signature should be:

```
(ctx::Context, choices::Vector{String}) -> Any 
```
