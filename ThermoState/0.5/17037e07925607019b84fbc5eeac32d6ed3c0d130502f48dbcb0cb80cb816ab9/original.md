```
mol_internal_energy(model,state::ThermodynamicState,unit,[options...])::Real
```

Keyword symbols: `:mol_u`, `:u`

Compute the molar internal energy (J/mol), from or using the specifications as base.

If you need unitful units, use the macro `@to_units` before the function call
