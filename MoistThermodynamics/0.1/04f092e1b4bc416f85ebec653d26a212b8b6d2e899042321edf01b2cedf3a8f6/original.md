```
 PhaseNonEquil{FT} <: ThermodynamicState
```

A thermodynamic state assuming thermodynamic non-equilibrium (therefore, temperature can be computed directly).

# Constructors

```
PhaseNonEquil(e_int, q::PhasePartition, ρ)
```

# Fields

  * `param_set`: parameter set (e.g., planet parameters)
  * `e_int`: internal energy
  * `ρ`: density of air (potentially moist)
  * `q`: phase partition
