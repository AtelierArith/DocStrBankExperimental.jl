```julia
BIC_int(data, model, params; kw...)

```

Estimate the Bayesian Information Criterion by sampling from the population. Keyword arguments `kw` are passed to [`mc_marginal_logp`](@ref).
