```
sinkhorn_stabilized_epsscaling(
    μ, ν, C, ε;
    scaling_factor=1//2, scaling_steps=5, absorb_tol=1_000, kwargs...
)
```

This method is deprecated, please use

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

instead.

See also: [`sinkhorn`](@ref), [`SinkhornEpsilonScaling`](@ref)
