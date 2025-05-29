```
counterTrigger_presamples(rp::RedPitaya)
```

Return the number of samples that the counter trigger should trigger prior to reaching the reference counter.

# Examples

```julia
julia> counterTrigger_presamples!(rp, 50)
true

julia> counterTrigger_presamples(rp)
50
```
