```
sinkhorn_stabilized(μ, ν, C, ε; absorb_tol=1_000, kwargs...)
```

このメソッドは非推奨です。代わりに以下を使用してください。

```julia
sinkhorn(
    μ, ν, C, ε, SinkhornStabilized(; absorb_tol=absorb_tol); kwargs...
)
```

関連情報: [`sinkhorn`](@ref), [`SinkhornStabilized`](@ref)
