```
mass_density(model,state::ThermodynamicState,unit,[options...])::Real
```

Keyword symbols: `:mass_rho`, `:mass_ρ`

Compute the specific (mass) density (kg/m³), from or using the specifications as base.

If you need unitful units, use the macro `@to_units` before the function call
