```
ess(chains::Chains; duration=compute_duration, kwargs...)
```

Estimate the effective sample size.

ESS per second options include `duration=MCMCChains.compute_duration` (the default) and `duration=MCMCChains.wall_duration`.
