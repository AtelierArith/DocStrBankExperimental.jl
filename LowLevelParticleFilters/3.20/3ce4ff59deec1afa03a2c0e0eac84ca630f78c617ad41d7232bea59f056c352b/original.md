```
AdvancedParticleFilter(N::Integer, dynamics::Function, measurement::Function, measurement_likelihood, dynamics_density, initial_density; p = NullParameters(), threads = false, kwargs...)
```

This type represents a standard particle filter but affords extra flexibility compared to the [`ParticleFilter`](@ref) type, e.g., non-additive noise in the dynamics and measurement functions.

See the docs for more information: https://baggepinnen.github.io/LowLevelParticleFilters.jl/stable/#AdvancedParticleFilter-1

# Arguments:

  * `N`: Number of particles
  * `dynamics`: A discrete-time dynamics function `(x, u, p, t, noise=false) -> x⁺`. It's important that the `noise` argument defaults to `false`.
  * `measurement`: A measurement function `(x, u, p, t, noise=false) -> y`. It's important that the `noise` argument defaults to `false`.
  * `measurement_likelihood`: A function `(x, u, y, p, t)->logl` to evaluate the log-likelihood of a measurement.
  * `dynamics_density`: This field is not used by the advanced filter and can be set to `nothing`.
  * `initial_density`: The distribution of the initial state.
  * `threads`: use threads to propagate particles in parallel. Only activate this if your dynamics is thread-safe. `SeeToDee.SimpleColloc` is not thread-safe by default due to the use of internal caches, but `SeeToDee.Rk4` is.

# Extended help

## Multiple measurement models

The `measurement_likelihood` function is used to evaluate the likelihood of a measurement. If you have multiple sensors and want to perform individual `correct!` steps for each, call `correct!(..., g = custom_likelihood_function)`.
