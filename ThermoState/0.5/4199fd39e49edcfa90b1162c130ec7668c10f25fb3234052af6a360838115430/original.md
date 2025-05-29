```
mass_volume(model,state::ThermodynamicState,unit,[options...])::Real
```

Keyword symbols: `:mass_v`

Compute the specific (mass) volume (m³/kg), from or using the specifications as base.

If you need unitful units, use the macro `@to_units` before the function call
