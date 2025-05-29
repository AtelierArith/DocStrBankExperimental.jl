```
ess(
    samples::AbstractArray{<:Union{Missing,Real}};
    kind=:bulk,
    relative::Bool=false,
    autocov_method=AutocovMethod(),
    split_chains::Int=2,
    maxlag::Int=250,
    kwargs...
)
```

Estimate the effective sample size (ESS) of the `samples` of shape `(draws, [chains[, parameters...]])` with the `autocov_method`.

Optionally, the `kind` of ESS estimate to be computed can be specified (see below). Some `kind`s accept additional `kwargs`.

If `relative` is `true`, the relative ESS is returned, i.e. `ess / (draws * chains)`.

`split_chains` indicates the number of chains each chain is split into. When `split_chains > 1`, then the diagnostics check for within-chain convergence. When `d = mod(draws, split_chains) > 0`, i.e. the chains cannot be evenly split, then 1 draw is discarded after each of the first `d` splits within each chain. There must be at least 3 draws in each chain after splitting.

`maxlag` indicates the maximum lag for which autocovariance is computed and must be greater than 0.

For a given estimand, it is recommended that the ESS is at least `100 * chains` and that $\widehat{R} < 1.01$.[^VehtariGelman2021]

See also: [`AutocovMethod`](@ref), [`FFTAutocovMethod`](@ref), [`BDAAutocovMethod`](@ref), [`rhat`](@ref), [`ess_rhat`](@ref), [`mcse`](@ref)

## Kinds of ESS estimates

If `kind` isa a `Symbol`, it may take one of the following values:

  * `:bulk`: basic ESS computed on rank-normalized draws. This kind diagnoses poor convergence   in the bulk of the distribution due to trends or different locations of the chains.
  * `:tail`: minimum of the quantile-ESS for the symmetric quantiles where   `tail_prob=0.1` is the probability in the tails. This kind diagnoses poor convergence in   the tails of the distribution. If this kind is chosen, `kwargs` may contain a   `tail_prob` keyword.
  * `:basic`: basic ESS, equivalent to specifying `kind=Statistics.mean`.

!!! note
    While Bulk-ESS is conceptually related to basic ESS, it is well-defined even if the chains do not have finite variance.[^VehtariGelman2021] For each parameter, rank-normalization proceeds by first ranking the inputs using "tied ranking" and then transforming the ranks to normal quantiles so that the result is standard normally distributed. This transform is monotonic.


Otherwise, `kind` specifies one of the following estimators, whose ESS is to be estimated:

  * [`Statistics.mean`](@extref)
  * [`Statistics.median`](@extref)
  * [`Statistics.std`](@extref)
  * [`StatsBase.mad`](@extref)
  * `Base.Fix2(Statistics.quantile, p::Real)`

[^VehtariGelman2021]: Vehtari, A., Gelman, A., Simpson, D., Carpenter, B., & Bürkner, P. C. (2021). Rank-normalization, folding, and localization: An improved $\widehat {R}$ for assessing convergence of MCMC. Bayesian Analysis. doi: [10.1214/20-BA1221](https://doi.org/10.1214/20-BA1221) arXiv: [1903.08008](https://arxiv.org/abs/1903.08008)
