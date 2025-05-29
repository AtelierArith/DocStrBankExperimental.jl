```
rhat(samples::AbstractArray{Union{Real,Missing}}; kind::Symbol=:rank, split_chains=2)
```

Compute the $\widehat{R}$ diagnostics for each parameter in `samples` of shape `(draws, [chains[, parameters...]])`.[^VehtariGelman2021]

`kind` indicates the kind of $\widehat{R}$ to compute (see below).

`split_chains` indicates the number of chains each chain is split into. When `split_chains > 1`, then the diagnostics check for within-chain convergence. When `d = mod(draws, split_chains) > 0`, i.e. the chains cannot be evenly split, then 1 draw is discarded after each of the first `d` splits within each chain.

See also [`ess`](@ref), [`ess_rhat`](@ref), [`rstar`](@ref)

## Kinds of $\widehat{R}$

The following `kind`s are supported:

  * `:rank`: maximum of $\widehat{R}$ with `kind=:bulk` and `kind=:tail`.
  * `:bulk`: basic $\widehat{R}$ computed on rank-normalized draws. This kind diagnoses   poor convergence in the bulk of the distribution due to trends or different locations of   the chains.
  * `:tail`: $\widehat{R}$ computed on draws folded around the median and then   rank-normalized. This kind diagnoses poor convergence in the tails of the distribution   due to different scales of the chains.
  * `:basic`: Classic $\widehat{R}$.

[^VehtariGelman2021]: Vehtari, A., Gelman, A., Simpson, D., Carpenter, B., & Bürkner, P. C. (2021). Rank-normalization, folding, and localization: An improved $\widehat {R}$ for assessing convergence of MCMC. Bayesian Analysis. doi: [10.1214/20-BA1221](https://doi.org/10.1214/20-BA1221) arXiv: [1903.08008](https://arxiv.org/abs/1903.08008)
