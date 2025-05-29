```julia
propagate!(
    orbit,
    Δt;
    stm,
    algorithm,
    reltol,
    abstol,
    kwargs...
)

```

Numerically integrate the orbit forward (or backward) in time, modifying the  state vector in-place within the `AstrodynamicalOrbit` instance.
