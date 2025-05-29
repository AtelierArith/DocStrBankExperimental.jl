```
liquid_fraction(param_set, T, phase_type[, q])
```

The fraction of condensate that is liquid where

  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details
  * `phase_type` a thermodynamic state type

# PhaseNonEquil behavior

If `q.liq` or `q.ice` are nonzero, the liquid fraction is computed from them.

# ThermodynamicState

Otherwise, phase equilibrium is assumed so that the fraction of liquid is a function that is 1 above `T_freeze` and goes to zero below `T_icenuc`.
