```
spinodal_pressure(model::EoSModel, T, x; v0, phase)
```

Calculates the spinodal pressure and volume for a given temperature and composition. Returns a tuple, containing:

  * spinodal pressure [`Pa`]
  * spinodal volume [`m³`]

Calculates either the liquid or the vapor spinodal point depending on the given starting volume `v0` or the `phase`. The keyword `phase` is ignored if `v0` is given.
