```
mass_entropy(model,state::ThermodynamicState,unit,[options...])::Real
```

Keyword symbols: `:mass_s`

Compute the specific (mass) entropy (J/(kg K)), from or using the specifications as base.

If you need unitful units, use the macro `@to_units` before the function call
