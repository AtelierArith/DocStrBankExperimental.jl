```
mass_helmholtz(model,state::ThermodynamicState,unit,[options...])::Real
```

Keyword symbols: `:mass_a`

Compute the specific (mass) helmholtz energy (J/kg), from or using the specifications as base.

If you need unitful units, use the macro `@to_units` before the function call
