```
simulate(T, model, θ; burnin, pinfirst)
```

Function to generate time series from Count Data model.

  * `T`: Length of time series
  * `model`: Model specification
  * `θ`: Parameters (vector or struct)
  * `burnin`: Number of burnin observations, default 500
  * `pinfirst`: Set values for first observations (instead of burnin)

# Example

```julia-repl
model = CountModel(pastObs = 1)
simulate(100, model, [10, 0.5])
```
