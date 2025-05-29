```julia
propagate(
    orbit,
    Δt;
    stm,
    algorithm,
    reltol,
    abstol,
    kwargs...
)

```

Numerically integrate the orbit forward (or backward) in time, and return a new  `AstrodynamicalOrbit` instance with identical parameters to the provided orbit.
