# hpdi

Compute high density region.

```julia
hpdi(x; alpha)

```

Derived from `hpd` in MCMCChains.jl.

By default alpha=0.11 for a 2-sided tail area of p < 0.055% and p > 0.945%.
