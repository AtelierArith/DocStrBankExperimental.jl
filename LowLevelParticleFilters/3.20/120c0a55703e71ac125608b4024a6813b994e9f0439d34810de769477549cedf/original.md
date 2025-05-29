```
ParticleFilteringSolution{F, Tu, Ty, Tx, Tw, Twe, Tll} <: AbstractFilteringSolution
```

# Fields:

  * `f`: The filter used to produce the solution.
  * `u`: Input
  * `y`: Output / measurements
  * `x`: Particles, the size of this array is `(N,T)`, where `N` is the number of particles and `T` is the number of time steps. Each element represents a weighted state hypothesis with weight given by `we`.
  * `w`: Weights (log space). These are used for internal computations.
  * `we`: Weights (exponentiated / original space). These are the ones to use to compute weighted means etc., they sum to one for each time step.
  * `ll`: Log likelihood

# Plot

The solution object can be plotted

```
plot(sol; nbinsy=30, xreal=nothing, dim=nothing, ploty=true, q=nothing)
```

By default, a weighted 2D histogram is plotted, one for each state variable. If a vector of quantiles are provided in `q`, the quantiles are plotted instead of the histogram. If `xreal` is provided, the true state is plotted as a scatter plot on top of the histogram. If `dim` is provided, only the specified dimension is plotted. If `ploty` is true, the measurements are plotted as well.
