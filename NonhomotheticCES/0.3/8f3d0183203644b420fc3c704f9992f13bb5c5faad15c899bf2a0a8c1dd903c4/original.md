```julia
log_sectoral_consumptions(U, p̂, Ê, Ĉ)

```

Calculate **log** sectoral consumptions, return as a vector. Arguments are in logs; see [`log_consumption_aggregator`](@ref) which whould also be used to obtain `Ĉ`.

The budget constraint holds, ie

```julia
logsumexp(log_sectoral_consumptions(U, p̂s, Ê, Ĉ) .+ p̂s) ≈ Ê
```
