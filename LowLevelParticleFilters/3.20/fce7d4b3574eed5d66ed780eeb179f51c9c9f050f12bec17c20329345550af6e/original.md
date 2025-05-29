```
ll = loglik(filter, u, y, p=parameters(filter))
ll = loglik(filter, u, y, x, p=parameters(filter))
```

Calculate log-likelihood for entire sequences `u,y`.

For Kalman-type filters when an accurate state sequence `x` is available, such as when data is obtained from a simulation or in a lab setting, the log-likelihood can be calculated using the state prediction errors rather than the output prediction errors. In this case, `logpdf(f.R, x-x̂)` is used rather than `logpdf(S, y-ŷ)`.
