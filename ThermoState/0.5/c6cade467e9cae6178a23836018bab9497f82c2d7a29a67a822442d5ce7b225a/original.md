```
mol_density(model,state::ThermodynamicState,unit,[options...])::Real
```

Keyword symbols: `:mol_rho`, `:rho`, `:mol_ρ`, `:ρ`

Compute the molar density (mol/m³), from or using the specifications as base.

If you need unitful units, use the macro `@to_units` before the function call
