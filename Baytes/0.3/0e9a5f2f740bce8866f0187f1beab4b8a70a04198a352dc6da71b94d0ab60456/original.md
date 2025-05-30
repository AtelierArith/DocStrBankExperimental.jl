```julia
propose!(_rng, trace, algorithmᵛ, modelᵛ, data)

```

Propose new parameter for each model in `modelᵛ` given `data` with algorithms `algorithmᵛ`. A separate model for each chain is provided to avoid pointer issues. If `args` is a single `SMC` algorithm, chains will not be separately allocated but instead used within the algorithm. Note that smc still works as intended if used alongside other mcmc sampler in `args`.

# Examples

```julia

```
