```
sinkhorn_stabilized(μ, ν, C, ε; absorb_tol=1_000, kwargs...)
```

This method is deprecated, please use

```julia
sinkhorn(
    μ, ν, C, ε, SinkhornStabilized(; absorb_tol=absorb_tol); kwargs...
)
```

instead.

See also: [`sinkhorn`](@ref), [`SinkhornStabilized`](@ref)
