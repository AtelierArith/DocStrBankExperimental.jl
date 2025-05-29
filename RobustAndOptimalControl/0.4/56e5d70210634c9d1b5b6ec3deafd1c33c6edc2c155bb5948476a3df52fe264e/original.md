```
ss2particles(G::Vector{<:AbstractStateSpace})
```

Converts a vector of state space models to a single state space model with coefficient type `MonteCarloMeasurements.Particles`.

See also [`sys_from_particles`](@ref).
