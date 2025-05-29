```
saturation_vapor_pressure(param_set, T, Liquid())
```

Return the saturation vapor pressure over a plane liquid surface given

  * `T` temperature
  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details

    `saturation_vapor_pressure(param_set, T, Ice())`

Return the saturation vapor pressure over a plane ice surface given

  * `T` temperature
  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details

    `saturation_vapor_pressure(param_set, T, LH_0, Δcp)`

Compute the saturation vapor pressure over a plane surface by integration of the Clausius-Clapeyron relation.

The Clausius-Clapeyron relation

```
`dlog(p_v_sat)/dT = [LH_0 + Δcp * (T-T_0)]/(R_v*T^2)`
```

is integrated from the triple point temperature `T_triple`, using Kirchhoff's relation

```
`L = LH_0 + Δcp * (T - T_0)`
```

for the specific latent heat `L` with constant isobaric specific heats of the phases. The linear dependence of the specific latent heat on temperature `T` allows analytic integration of the Clausius-Clapeyron relation to obtain the saturation vapor pressure `p_v_sat` as a function of the triple point pressure `press_triple`.
