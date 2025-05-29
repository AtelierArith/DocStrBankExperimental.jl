```
liquid_fraction(T[, q::PhasePartition])
```

The fraction of condensate that is liquid where

  * `T` temperature
  * `q` [`PhasePartition`](@ref)

If `q.liq` or `q.ice` are nonzero, the liquid fraction is computed from them.

Otherwise, phase equilibrium is assumed so that the fraction of liquid is a function that is 1 above `T_freeze` and goes to zero below `T_freeze`.
