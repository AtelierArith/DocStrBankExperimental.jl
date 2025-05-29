```
mol_enthalpy(model,state::ThermodynamicState,unit,[options...])::Real
```

Keyword symbols: `:mol_h`, `:h`

Compute the molar enthalpy (J/mol), from or using the specifications as base.

If you need unitful units, use the macro `@to_units` before the function call
