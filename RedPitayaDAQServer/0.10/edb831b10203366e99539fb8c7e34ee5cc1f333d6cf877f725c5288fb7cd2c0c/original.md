```
counterTrigger_reset(rp::RedPitaya)
```

Return the reset status of the counter trigger.

# Example

```julia
julia> counterTrigger_reset!(rp, true)

julia>counterTrigger_reset(rp)
true
```
