```
 PhaseNonEquil{FT} <: ThermodynamicState
```

A thermodynamic state assuming thermodynamic non-equilibrium (therefore, temperature can be computed directly).

# Constructors

```
PhaseNonEquil(param_set, e_int, q::PhasePartition, ρ)
```

# Fields

  * `e_int`: internal energy
  * `ρ`: density of air (potentially moist)
  * `q`: phase partition
