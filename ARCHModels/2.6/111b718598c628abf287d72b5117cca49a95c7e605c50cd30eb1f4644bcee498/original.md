```
fit(am::ARCHModel; algorithm=BFGS(), autodiff=:forward, kwargs...)
```

Fit the uni- or multivariate ARCHModel specified by `am` and return the result in a new instance of `ARCHModel`. Keyword arguments are passed on to the optimizer.
