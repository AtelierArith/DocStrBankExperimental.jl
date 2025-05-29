```
mol_gibbs(model,state::ThermodynamicState,unit,[options...])::Real
```

Keyword symbols: `:mol_g`, `:g`

Compute the molar gibbs energy (J/mol), from or using the specifications as base.

If you need unitful units, use the macro `@to_units` before the function call
