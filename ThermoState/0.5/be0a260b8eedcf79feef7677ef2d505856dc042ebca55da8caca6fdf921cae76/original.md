```
mass_gibbs(model,state::ThermodynamicState,unit,[options...])::Real
```

Keyword symbols: `:mass_g`

Compute the specific (mass) gibbs energy (J/kg), from or using the specifications as base.

If you need unitful units, use the macro `@to_units` before the function call
