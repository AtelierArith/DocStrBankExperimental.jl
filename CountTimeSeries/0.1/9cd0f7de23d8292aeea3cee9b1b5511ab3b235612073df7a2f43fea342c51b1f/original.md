```
ll(y, model, θ; initiate = "first")
```

Likelihood function for Count Data models.

  * `y`: Time series
  * `model`: Model Specification
  * `θ`: Parameters (Vector or parameter)
  * `initiate`: How is the time series initiated?

The time series can be initiated by "first", the first observed value, "intercept", the intercept parameter (possibly exponentiated if log-link), or "marginal", the marginal mean of the process.

# Example

```julia-repl
ll(y, model, pars)
```
