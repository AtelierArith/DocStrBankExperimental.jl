```
counterTrigger_reset!(rp::RedPitaya, val::Bool)
```

Set the reset of the counter trigger to `val`. Return `true` if the command was successful.

# Example

```julia
julia> counterTrigger_reset!(rp, true)
true

julia>counterTrigger_reset(rp)
true
```
