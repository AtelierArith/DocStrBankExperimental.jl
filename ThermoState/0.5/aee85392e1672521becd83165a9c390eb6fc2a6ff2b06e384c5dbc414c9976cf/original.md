```
total_volume(model,state::ThermodynamicState,unit,[options...])::Real
```

Keyword symbols: `:total_v`, `:V`

Compute the total volume (m³), from or using the specifications as base.

If you need unitful units, use the macro `@to_units` before the function call
