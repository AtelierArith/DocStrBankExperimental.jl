```
DensityRatioWeighting(tdata, [vars]; [options])
```

Density ratio weights based on empirical distribution of variables in target data `tdata`. Default to all variables.

## Optional parameters

  * `estimator` - Density ratio estimator (default to `LSIF()`)
  * `optlib`    - Optimization library (default to `default_optlib(estimator)`)

### Notes

Estimators from [DensityRatioEstimation.jl](https://github.com/JuliaML/DensityRatioEstimation.jl) are supported.
