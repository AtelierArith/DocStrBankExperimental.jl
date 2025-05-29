```julia
pool_posterior_matrices(results)

```

Given a vector of `results`, each containing a property `posterior_matrix` (eg obtained from [`mcmc_with_warmup`](@ref) with the same sample length), return a lazy view as an array indexed by `[parameter_index, pooled_draw_index]`.

This is useful for posterior analysis after diagnostics (see eg `Base.eachcol`).
