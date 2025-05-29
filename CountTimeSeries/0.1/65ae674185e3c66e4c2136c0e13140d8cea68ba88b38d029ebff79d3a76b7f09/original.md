```
var(model, θ)
```

Marginal variance of INARMA(p, q) process. Models with regressors are not covered.

  * `model`: Model specification
  * `θ`: Parameters (Vector or parameter type)

# Examples

```julia-repl
model = Model(model = "INARMA", pastObs = 1)
var(model, [10, 0.5])
```
