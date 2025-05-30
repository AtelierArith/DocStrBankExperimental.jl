```julia
construct(
    _rng,
    model,
    data,
    default,
    tempering,
    datatune,
    chains,
    updatesampler,
    args
)

```

Construct `chains` MCMC chains and initiate all algorithms stated in `args` separately. A separate model for each chain is provided to avoid pointer issues. If `args` is a single `SMC` algorithm, chains will not be separately allocated but instead used within the algorithm. Note that smc still works as intended if used alongside other mcmc sampler in `args`.

# Examples

```julia

```
