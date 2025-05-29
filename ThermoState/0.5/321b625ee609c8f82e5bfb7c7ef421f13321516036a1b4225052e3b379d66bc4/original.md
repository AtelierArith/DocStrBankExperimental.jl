```
mass_internal_energy(model,state::ThermodynamicState,unit,[options...])::Real
```

Keyword symbols: `:mass_u`

Compute the specific (mass) internal energy (J/kg), from or using the specifications as base.

If you need unitful units, use the macro `@to_units` before the function call
