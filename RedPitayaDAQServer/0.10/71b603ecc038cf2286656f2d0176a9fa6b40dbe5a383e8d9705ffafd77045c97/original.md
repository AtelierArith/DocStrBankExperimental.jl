counterTrigger_referenceCounter!(rp::RedPitaya, presamples)

Set the number of samples that the counter trigger should trigger on.

# Examples

```julia
julia> counterTrigger_referenceCounter(rp, 250)
true

julia> counterTrigger_referenceCounter!(rp)
250
```
