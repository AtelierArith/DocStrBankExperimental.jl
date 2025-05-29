```
rstar(
    rng::Random.AbstractRNG=Random.default_rng(),
    classifier,
    samples,
    chain_indices::AbstractVector{Int};
    subset::Real=0.7,
    split_chains::Int=2,
    verbosity::Int=0,
)
```

Compute the $R^*$ convergence statistic of the table `samples` with the `classifier`.

`samples` must be either an `AbstractMatrix`, an `AbstractVector`, or a table (i.e. implements the Tables.jl interface) whose rows are draws and whose columns are parameters.

`chain_indices` indicates the chain ids of each row of `samples`.

This method supports ragged chains, i.e. chains of nonequal lengths.
