```
PhaseEquil{FT} <: AbstractPhaseEquil
```

A thermodynamic state assuming thermodynamic equilibrium (therefore, saturation adjustment may be needed).

# Constructors

```
PhaseEquil(param_set, ρ, e_int, q_tot)
```

# Fields

  * `ρ`: density of air (potentially moist)
  * `p`: air pressure
  * `e_int`: internal energy
  * `q_tot`: total specific humidity
  * `T`: temperature: computed via [`saturation_adjustment`](@ref)
