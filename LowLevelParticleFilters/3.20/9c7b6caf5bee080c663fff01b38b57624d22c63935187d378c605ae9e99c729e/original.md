```
sol = forward_trajectory(pf, u::AbstractVector, y::AbstractVector, p=parameters(pf))
```

Run the particle filter for a sequence of inputs and measurements (offline / batch filtering). Return a solution with `x,w,we,ll = particles, weights, expweights and loglikelihood`

If [MonteCarloMeasurements.jl](https://github.com/baggepinnen/MonteCarloMeasurements.jl) is loaded, you may transform the output particles to `Matrix{MonteCarloMeasurements.Particles}` using `Particles(x,we)`. Internally, the particles are then resampled such that they all have unit weight. This is conventient for making use of the [plotting facilities of MonteCarloMeasurements.jl](https://baggepinnen.github.io/MonteCarloMeasurements.jl/stable/#Plotting-1).

`sol` can be plotted

```
plot(sol::ParticleFilteringSolution; nbinsy=30, xreal=nothing, dim=nothing)
```
