```
clear_sstate!(model; lvl=0.1, slp=0.0, <options>)
```

Set the steady state values to the provided defaults and presolve.

### Arguments

  * `model` - the model instance
  * `lvl`, `slp` - the initial guess for the level and the slope. Each could be a number or a vector of length equal to the number of variable in the model. Variables include regular and exogenous variables, but not shocks (shocks are assumed to be 0 in steady state).

### Options

Standard options (default values are taken from `model.options`)

  * `verbose`
