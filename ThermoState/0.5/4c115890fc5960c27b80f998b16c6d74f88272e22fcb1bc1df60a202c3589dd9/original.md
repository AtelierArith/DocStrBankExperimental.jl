```
mol_entropy(model,state::ThermodynamicState,unit,[options...])::Real
```

Keyword symbols: `:mol_s`, `:s`

Compute the molar entropy (J/(mol K)), from or using the specifications as base.

If you need unitful units, use the macro `@to_units` before the function call
