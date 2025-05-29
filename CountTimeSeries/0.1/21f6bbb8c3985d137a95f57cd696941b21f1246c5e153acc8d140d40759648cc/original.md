```
mean(model, θ)
```

Marginal mean of INARMA(p, q) process. Models with regressors are not covered.

  * `model`: Model specification
  * `θ`: Parameters (Vector or parameter type)

# Examples

```julia-repl
model = Model(model = "INARMA", pastObs = 1)
mean(model, [10, 0.5])
```
