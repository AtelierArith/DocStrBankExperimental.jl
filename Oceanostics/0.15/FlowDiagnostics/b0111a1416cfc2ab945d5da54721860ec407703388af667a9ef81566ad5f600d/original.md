```julia
DirectionalErtelPotentialVorticity(
    model,
    direction;
    tracer,
    location
)

```

Calculate the contribution from a given `direction` to the Ertel Potential Vorticity basde on a `model` and a `direction`. The Ertel Potential Vorticity is defined as

```
EPV = ωₜₒₜ ⋅ ∇b
```

where ωₜₒₜ is the total (relative + planetary) vorticity vector, `b` is the buoyancy and ∇ is the gradient operator.
