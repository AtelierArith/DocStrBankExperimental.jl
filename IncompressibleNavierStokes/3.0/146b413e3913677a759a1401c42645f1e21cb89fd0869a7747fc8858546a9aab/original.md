```julia
smagorinsky_closure(
    setup
) -> IncompressibleNavierStokes.var"#closure#182"

```

Create Smagorinsky closure model `m`. The model is called as `m(u, θ)`, where the Smagorinsky constant `θ` should be a scalar between `0` and `1` (for example `θ = 0.1`).
