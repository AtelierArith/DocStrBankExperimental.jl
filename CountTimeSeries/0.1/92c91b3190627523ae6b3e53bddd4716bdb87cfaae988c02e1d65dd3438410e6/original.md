```
mean(model, θ, ofλ = false)
```

Marginal mean of INGARCH(p, q) process. Models with regressors or a logarithmic link are not covered.

  * `model`: Model specification
  * `θ`: Parameters (Vector or parameter type)
  * `ofλ`: If true, the marginal mean of the conditional mean sequence is returned

# Examples

```julia-repl
model = Model(pastObs = 1)
mean(model, [10, 0.5])
```
