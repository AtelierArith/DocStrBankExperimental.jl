```
total_entropy(model,state::ThermodynamicState,unit,[options...])::Real
```

Keyword symbols: `:total_s`

Compute the total entropy (J/K), from or using the specifications as base.

If you need unitful units, use the macro `@to_units` before the function call
