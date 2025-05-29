```
total_helmholtz(model,state::ThermodynamicState,unit,[options...])::Real
```

Keyword symbols: `:total_a`

Compute the total helmholtz energy (J), from or using the specifications as base.

If you need unitful units, use the macro `@to_units` before the function call
