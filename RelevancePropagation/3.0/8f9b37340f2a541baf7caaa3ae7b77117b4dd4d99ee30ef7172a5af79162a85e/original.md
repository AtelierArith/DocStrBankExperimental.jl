```
ChainTuple(xs)
```

Thin wrapper around `Tuple` for use with Flux.jl models.

Combining [`ChainTuple`](@ref), [`ParallelTuple`](@ref) and [`SkipConnectionTuple`](@ref), data `xs` can be stored while preserving the structure of a Flux model without risking type piracy.
