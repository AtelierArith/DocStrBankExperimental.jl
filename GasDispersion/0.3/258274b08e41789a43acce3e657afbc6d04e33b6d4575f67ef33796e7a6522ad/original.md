```
plume(scenario::Scenario, model::PlumeModel[, equationset::EquationSet])
```

Runs the plume dispersion model on the given scenario and returns the solution which is callable to give the concentration     c(x, y, z[, t])

The concentration is in vol fraction, if `model` is unspecified, defaults to a simple gaussian plume model.

`equationset`s are used to specify that an alternative set of correlations  should be used for model parameters, if alternatives exist.

All model parameters are assumed to be in SI base units (i.e. distances in m, velocities in m/s, mass in kg, etc.)
