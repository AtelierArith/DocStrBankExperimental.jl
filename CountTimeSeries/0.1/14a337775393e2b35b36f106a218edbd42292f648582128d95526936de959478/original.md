```
acvf(model, θ, lagMax, ofλ)
```

Autocovariance function of INGARCH(p, q) process. Models with regressors or logarithmic link are not covered.

  * `model`: Model specification
  * `θ`: Parameters (Vector or parameter type)
  * `lagMax`: Maximum lag to be computed
  * `ofλ`: If true, return ACVF/ACF of conditional mean sequence

# Examples

```julia-repl
model = Model(pastObs = 1)
acvf(model, [10, 0.5])
```
