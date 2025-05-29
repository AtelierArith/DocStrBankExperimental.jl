```
fit!(am::ARCHModel; algorithm=BFGS(), autodiff=:forward, kwargs...)
```

Fit the uni- or multivariate ARCHModel specified by `am`, modifying `am` in place. Keyword arguments are passed on to the optimizer.
