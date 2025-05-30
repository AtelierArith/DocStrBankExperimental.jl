```
ess_rhat(chains::Chains; duration=compute_duration, kwargs...)
```

Estimate the effective sample size and the $\widehat{R}$ diagnostic

ESS per second options include `duration=MCMCChains.compute_duration` (the default) and `duration=MCMCChains.wall_duration`.
