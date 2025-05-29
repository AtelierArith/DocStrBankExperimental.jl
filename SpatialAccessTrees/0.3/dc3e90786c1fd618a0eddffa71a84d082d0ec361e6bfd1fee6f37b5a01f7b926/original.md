```
BeamSearchMultiSat(sat::Vector{SatType}; bsize=8, Δ=1f0) where {SatType<:Sat}
```

Applies beam search on a multi SAT array. See [`optimize!`](@ref) to tune the index for some objective.
