```
TemperatureRamp <: Method
```

Solves the system by iteratively solving systems of decreasing Temperature, using the previous solution as initial guess at a lower temperature. This may help deal with convergence issues.

Arguments

  * `method`: method by which to solve the system for individual temperatures.
  * `temperatures`: temperatures to consider. Must be a vector of increasing values.
  * `verbose`: whether to print information.

Example: `TemperatureRamp(NgIteration(), [0.1, 0.3, 0.4]; verbose=false)`
