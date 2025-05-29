```
saturation_excess(T, ρ, q::PhasePartition)
```

The saturation excess in equilibrium where

  * `T` temperature
  * `ρ` (moist-)air density
  * `q` [`PhasePartition`](@ref)

The saturation excess is the difference between the total specific humidity `q.tot` and the saturation specific humidity in equilibrium, and it is defined to be nonzero only if this difference is positive.
