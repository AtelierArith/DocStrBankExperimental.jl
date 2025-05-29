```
PhaseEquil{FT} <: ThermodynamicState
```

A thermodynamic state assuming thermodynamic equilibrium (therefore, saturation adjustment may be needed).

# Constructors

```
PhaseEquil(e_int, ρ, q_tot)
```

# Fields

  * `param_set`: parameter set (e.g., planet parameters)
  * `e_int`: internal energy
  * `ρ`: density of air (potentially moist)
  * `q_tot`: total specific humidity
  * `T`: temperature: computed via [`saturation_adjustment`](@ref)
