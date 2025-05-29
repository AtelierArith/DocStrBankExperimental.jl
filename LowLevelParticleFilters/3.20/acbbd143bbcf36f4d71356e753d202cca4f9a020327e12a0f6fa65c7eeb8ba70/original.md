```
ParticleFilter(N::Integer, dynamics, measurement, dynamics_density, measurement_density, initial_density; threads = false, p = NullParameters(), kwargs...)
```

See the docs for more information: https://baggepinnen.github.io/LowLevelParticleFilters.jl/stable/#Particle-filter-1

# Arguments:

  * `N`: Number of particles
  * `dynamics`: A discrete-time dynamics function `(x, u, p, t) -> x⁺`
  * `measurement`: A measurement function `(x, u, p, t) -> y`
  * `dynamics_density`: A probability-density function for additive noise in the dynamics. Use [`AdvancedParticleFilter`](@ref) for non-additive noise.
  * `measurement_density`: A probability-density function for additive measurement noise. Use [`AdvancedParticleFilter`](@ref) for non-additive noise.
  * `initial_density`: Distribution of the initial state.
