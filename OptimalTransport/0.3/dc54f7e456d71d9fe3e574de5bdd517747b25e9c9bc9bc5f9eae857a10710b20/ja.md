```
sinkhorn_stabilized_epsscaling(
    μ, ν, C, ε;
    scaling_factor=1//2, scaling_steps=5, absorb_tol=1_000, kwargs...
)
```

このメソッドは非推奨です。代わりに以下を使用してください。

```julia
sinkhorn(
    μ,
    ν,
    C,
    ε,
    SinkhornEpsilonScaling(
        SinkhornStabilized(; absorb_tol=absorb_tol);
        factor=scaling_factor,
        steps=scaling_steps,
    );
    kwargs...,
)
```

詳細については、[`sinkhorn`](@ref)、[`SinkhornEpsilonScaling`](@ref)を参照してください。
