```
acvf(model, θ, lagMax)
```

Autocovariance function of INARMA(p, q) process. Models with regressors are not covered.

  * `model`: Model specification
  * `θ`: Parameters (Vector or parameter type)
  * `lagMax`: Maximum lag to be computed

# Examples

```julia-repl
model = Model(model = "INARMA", pastObs = 1)
acvf(model, [10, 0.5])
```
