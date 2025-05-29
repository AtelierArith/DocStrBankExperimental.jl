```
BLS(t, y, [yerr];
    duration, periods=autoperiod(t, duration, kwargs...), 
    objective=:likelihood, oversample=10, kwargs...)
```

Compute the box-least-squares periodogram.

# Parameters

  * `t` - the time for each observation. Units are irrelevant, except that they must be consistent for all temporal parameters (e.g., `duration`). `Unitful.jl` units work seamlessly without needing to convert.
  * `y` - the flux value for each observation
  * `yerr`, optional - the uncertainty for each observation, if not provided, will default to ones
  * `duration` - The duration or durations to consider. Same units as `t`
  * `periods`, optional - The period grid to computer the BLS power over. If not provided, [`autoperiod`](@ref) will be called along with any extra keyword arguments (like `minimum_period`)
  * `objective`, optional - Choose between maximizing the likeilhood (`:likeilhood`, default) or the signal-to-noise ratio (`:snr`).
  * `oversample`, optional - The number of bins per duration that should be used. Larger values of `oversample` will lead to a finer grid.

The returned values are wrapped into a convenience type [`BoxLeastSquares.BLSPeriodogram`](@ref)
