```
IterControl{S}
IterControl(n::Int, base::Int, masks, factors) -> IterControl
```

Iterator to iterate through controlled subspace. See also [`itercontrol`](@ref).  `S` is the number of chunks,  `n` is the size of Hilbert space,  `base` is the base of counter,  `masks` and `factors` are helpers for enumerating over the target Hilbert Space.
