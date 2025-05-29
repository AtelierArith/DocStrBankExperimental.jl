```
spinodal_temperature(model::EoSModel, p, x; T0, v0, phase)
```

Calculates the spinodal pressure and volume for a given pressure and composition. Returns a tuple, containing:

  * spinodal temperature [`K`]
  * spinodal volume [`m³`]

Calculates either the liquid or the vapor spinodal point depending on the given starting temperature `T0` and volume `v0` or the `phase`. The keyword `phase` is ignored if `T0` or `v0` is given.
