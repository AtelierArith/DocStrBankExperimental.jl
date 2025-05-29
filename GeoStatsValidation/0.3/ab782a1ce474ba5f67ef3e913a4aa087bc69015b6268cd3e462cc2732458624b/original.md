```
DensityRatioValidation(k; [options])
```

Density ratio validation where weights are first obtained with density ratio estimation, and then used in `k`-fold weighted cross-validation.

## Options

  * `shuffle`   - Shuffle the data before folding (default to `true`)
  * `estimator` - Density ratio estimator (default to `LSIF()`)
  * `optlib`    - Optimization library (default to `default_optlib(estimator)`)
  * `lambda`    - Power of density ratios (default to `1.0`)
  * `loss`      - Dictionary with loss functions (default to `Dict()`)

Please see [DensityRatioEstimation.jl](https://github.com/JuliaEarth/DensityRatioEstimation.jl) for a list of supported estimators.

## References

  * Hoffimann et al. 2020. [Geostatistical Learning: Challenges and Opportunities](https://arxiv.org/abs/2102.08791)
