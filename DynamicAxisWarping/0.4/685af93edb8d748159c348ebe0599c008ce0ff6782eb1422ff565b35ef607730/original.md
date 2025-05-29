```
struct DTW{D,N} <: DTWDistance{D}
```

# Keyword arguments:

  * `radius`: The maximum allowed deviation of the matching path from the diagonal
  * `dist`: Inner distance
  * `transportcost` If >1, an additional penalty factor for non-diagonal moves is added.
  * `normalizer`: defaults to `Nothing`. Supported options are the normalizers defined in [SlidingDistancesBase.jl](https://github.com/baggepinnen/SlidingDistancesBase.jl)

If the two time-series are of equal length, [`dtw_cost`](@ref) is called, if not, [`dtwnn`](@ref) is called.
