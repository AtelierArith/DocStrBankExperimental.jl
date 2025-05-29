```
ess(p::AbstractParticles{T,N})
```

Calculates the effective sample size. This is useful if particles come from MCMC sampling and are correlated in time. The ESS is a number between [0,N].

Initial source: https://github.com/tpapp/MCMCDiagnostics.jl
