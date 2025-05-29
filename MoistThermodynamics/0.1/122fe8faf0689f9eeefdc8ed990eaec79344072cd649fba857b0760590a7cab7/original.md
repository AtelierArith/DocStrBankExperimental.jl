```
PhasePartition
```

Represents the mass fractions of the moist air mixture.

# Constructors

```
PhasePartition(q_tot::Real[, q_liq::Real[, q_ice::Real]])
PhasePartition(ts::ThermodynamicState)
```

See also [`PhasePartition_equil`](@ref)

# Fields

  * `tot`: total specific humidity
  * `liq`: liquid water specific humidity (default: `0`)
  * `ice`: ice specific humidity (default: `0`)
