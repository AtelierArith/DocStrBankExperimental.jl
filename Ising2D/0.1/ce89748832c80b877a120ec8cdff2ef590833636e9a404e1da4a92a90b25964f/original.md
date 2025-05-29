```
histogram_mcmc_ising2d(S, E=nothing, M=nothing;
    niters=length(S), bin=min(100, max(10, round(Int, 1.2*√niters))), 
    size=(600, 200), kwargs...
)
```

plots the histogram of energy per site and magnetization of the MCMC result S.
