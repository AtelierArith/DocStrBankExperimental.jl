```
molar_mass(model,state::ThermodynamicState,unit,[options...])::Real
```

Compute the amount of mass per unit of moles (in kg/mol) of the provided state, from or using the specifications as base.

If you need unitful units, use the macro `@to_units` before the function call
