```
total_internal_energy(model,state::ThermodynamicState,unit,[options...])::Real
```

Keyword symbols: `:total_u`

Compute the total internal energy (J), from or using the specifications as base.

If you need unitful units, use the macro `@to_units` before the function call
