```
q_vap_saturation_generic(param_set, T, ρ[, phase=Liquid()])
```

Compute the saturation specific humidity over a plane surface of condensate, given

```
- `param_set`: an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details
- `T`: temperature
- `ρ`: air density
- (optional) `Liquid()`: indicating condensate is liquid
- (optional) `Ice()`: indicating condensate is ice
```
