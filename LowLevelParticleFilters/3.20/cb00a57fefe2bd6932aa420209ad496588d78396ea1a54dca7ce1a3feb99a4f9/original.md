```
x,u,y = simulate(f::AbstractFilter, T::Int, du::Distribution, p=parameters(f), [N]; dynamics_noise=true, measurement_noise=true)
x,u,y = simulate(f::AbstractFilter, u, p=parameters(f); dynamics_noise=true, measurement_noise=true)
```

Simulate dynamical system forward in time `T` steps, or for the duration of `u`. Returns state sequence, inputs and measurements.

  * `u` is an input-signal trajectory, alternatively, `du` is a distribution of random inputs.

A simulation can be considered a draw from the prior distribution over the evolution of the system implied by the selected noise models. Such a simulation is useful in order to evaluate whether or not the noise models are reasonable.

If [MonteCarloMeasurements.jl](https://github.com/baggepinnen/MonteCarloMeasurements.jl) is loaded, the argument `N::Int` can be supplied, in which case `N` simulations are done and the result is returned in the form of `Vector{MonteCarloMeasurements.Particles}`.
