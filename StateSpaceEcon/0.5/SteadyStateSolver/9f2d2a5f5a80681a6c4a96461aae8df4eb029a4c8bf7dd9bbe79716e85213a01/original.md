```
check_sstate(model; <options>)
```

Run a diagnostic test to determine if the steady state solution stored within the given model object is indeed a solution of the steady state system of equations.

Return the number of steady state equations that are violated by the current steady state solution. If `verbose=true`, also display diagnostic information in the form of listing all bad equations and their residuals.

### Options

Standard options (default values from `model.options`)

  * `verbose`
  * `tol` - an equation is considered satisfied if its residual, in absolute value, is smaller than this number.
