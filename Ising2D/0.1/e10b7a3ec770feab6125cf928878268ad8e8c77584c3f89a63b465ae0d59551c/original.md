```
plot_mcmc_ising2d(S, E=nothing, M=nothing;
    k=1.0, β=k*β_ising2d, niters=length(S), t=niters,   
    ylim_E=(-1.50, -1.35), ylim_M=(-0.75, 0.75), lw=0.5, alpha=0.8,
    size=(600, 300), color=:gist_earth, clim=(-2, 1.1), kwargs...
)
```

plots the MCMC result S with energy per site and magnetization.
