```
total_enthalpy(model,state::ThermodynamicState,unit,[options...])::Real
```

Keyword symbols: `:total_h`

Compute the total enthalpy (J), from or using the specifications as base.

If you need unitful units, use the macro `@to_units` before the function call
