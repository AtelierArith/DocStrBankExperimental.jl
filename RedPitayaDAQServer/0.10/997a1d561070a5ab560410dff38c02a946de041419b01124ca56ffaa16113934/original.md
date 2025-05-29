```
counterTrigger_referenceCounter(rp::RedPitaya)
```

Return the counter value that the counter trigger should trigger on.

# Examples

```julia
julia> counterTrigger_referenceCounter!(rp, 250)
true

julia> counterTrigger_referenceCounter(rp)
250
```
