```
mol_number(model,state::ThermodynamicState,unit,[options...])::AbstractVector
```

Keyword symbols: `:n`

Compute the amount of moles (in mol) of each present compound present in the provided system, from or using the specifications as base.

If you need unitful units, use the macro `@to_units` before the function call
