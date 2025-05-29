```
UnitHydrograph{N, ST} <: AbstractHydrograph
```

Represents a Unit Hydrograph routing component.

# Fields

  * `uh_func::Function`: Function defining the unit hydrograph shape based on time and parameters.
  * `max_lag_func::Function`: Function calculating the maximum lag time based on parameters.
  * `infos::NamedTuple`: Metadata (inputs, outputs, params).

# Constructor

```julia
UnitHydrograph(inputs, params; uh_pairs, max_lag, outputs=[], configs=(solvetype=:DISCRETE, suffix=:_lag), name=nothing)
```

  * `inputs`, `params`, `outputs`: Vectors of `Num` variables.
  * `uh_pairs`: Vector of `Pair` defining piecewise UH segments (`time_bound => expression`).
  * `max_lag`: Upper bound for the first UH segment.
  * `configs`: NamedTuple containing `solvetype` (`:DISCRETE` or `:SPARSE`) and `suffix` for default output names.
  * `name`: Optional symbol identifier.

# Notes

  * The type parameter `ST` reflects the `solvetype` (`:DISCRETE` or `:SPARSE`).
  * Generates `uh_func` and `max_lag_func` from `uh_pairs` and `params`.
  * Used to convolve input time series with the defined unit hydrograph.
