```
octoplot(
    system::Octofitter.Model,
    chain::MCMCChains.Chains;
    fname="$(system.name)-plot-grid",
    color = "$(first(keys(system.planets)))_e",
    colorbartitle=string(color),
    clims = quantile(vec(chain[color]),(0.01, 0.99)),
    cmap = :plasma,
    dpi=200,
    kwargs...
)
```

Given a  `LogDensityModel` and an MCMC Chain (sampled either from  the posterior or the prior), produce a panel of 9 plots visualizing the orbits. The output is saved to a file based on the name of the system (`fname`).
