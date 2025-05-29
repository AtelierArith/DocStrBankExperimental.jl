```
mass_enthalpy(model,state::ThermodynamicState,unit,[options...])::Real
```

Keyword symbols: `:mass_h`

Compute the specific (mass) enthalpy (J/kg), from or using the specifications as base.

If you need unitful units, use the macro `@to_units` before the function call
