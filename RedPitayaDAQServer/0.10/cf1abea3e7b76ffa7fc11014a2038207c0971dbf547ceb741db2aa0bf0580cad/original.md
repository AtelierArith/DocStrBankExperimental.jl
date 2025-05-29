```
triggerPropagation!(rp::RedPitaya, val::Bool)
```

Set the trigger propagation of the RedPitaya to `val`. Return `true` if the command was successful.

# Example

```julia
julia> triggerPropagation!(rp, true)
true

julia>triggerPropagation(rp)
true
```
