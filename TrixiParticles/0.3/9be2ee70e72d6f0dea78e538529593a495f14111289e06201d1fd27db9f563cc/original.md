```
DensityReinitializationCallback(; interval::Integer=0, dt=0.0)
```

Callback to reinitialize the density field when using [`ContinuityDensity`](@ref) [Panizzo2007](@cite).

# Keywords

  * `interval=0`:              Reinitialize the density every `interval` time steps.
  * `dt`:                      Reinitialize the density in regular intervals of `dt` in terms                            of integration time.
  * `reinit_initial_solution`: Reinitialize the initial solution (default=false)
