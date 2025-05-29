```
acf(model, θ, lagMax)
```

Autocorrelation function of INARMA(p, q) process. Models with regressors are not covered.

  * `model`: Model specification
  * `θ`: Parameters (Vector or parameter type)
  * `lagMax`: Maximum lag to be computed

# Examples

```julia-repl
model = Model(model = "INARMA", pastObs = 1)
acf(model, [10, 0.5])
```
