```
mass(model,state::ThermodynamicState,unit,[options...])::Real
```

Keyword symbols: `:mass`

Compute the total amount of mass (in kg) of the provided system, from or using the specifications as base.

If you need unitful units, use the macro `@to_units` before the function call
