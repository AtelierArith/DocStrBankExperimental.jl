```
total_energy(e_kin, e_pot, T[, q::PhasePartition])
```

The total energy per unit mass, given

  * `e_kin` kinetic energy per unit mass
  * `e_pot` potential energy per unit mass
  * `T` temperature

and, optionally,

  * `q` [`PhasePartition`](@ref). Without this argument, the results are for dry air.
