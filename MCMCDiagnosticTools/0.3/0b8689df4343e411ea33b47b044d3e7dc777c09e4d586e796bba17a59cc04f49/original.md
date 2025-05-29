```
mcse(samples::AbstractArray{<:Union{Missing,Real}}; kind=Statistics.mean, kwargs...)
```

Estimate the Monte Carlo standard errors (MCSE) of the estimator `kind` applied to `samples` of shape `(draws, [chains[, parameters...]])`.

See also: [`ess`](@ref)

## Kinds of MCSE estimates

The estimator whose MCSE should be estimated is specified with `kind`. `kind` must accept a vector of the same `eltype` as `samples` and return a real estimate.

For the following estimators, the effective sample size [`ess`](@ref) and an estimate of the asymptotic variance are used to compute the MCSE, and `kwargs` are forwarded to `ess`:

  * [`Statistics.mean`](@extref)
  * [`Statistics.median`](@extref)
  * [`Statistics.std`](@extref)
  * `Base.Fix2(Statistics.quantile, p::Real)`

For other estimators, the subsampling bootstrap method (SBM)[^FlegalJones2011][^Flegal2012] is used as a fallback, and the only accepted `kwargs` are `batch_size`, which indicates the size of the overlapping batches used to estimate the MCSE, defaulting to `floor(Int, sqrt(draws * chains))`. Note that SBM tends to underestimate the MCSE, especially for highly autocorrelated chains. One should verify that autocorrelation is low by checking the bulk- and tail-ESS values.

[^FlegalJones2011]: Flegal JM, Jones GL. (2011) Implementing MCMC: estimating with confidence.                 Handbook of Markov Chain Monte Carlo. pp. 175-97.                 [pdf](http://faculty.ucr.edu/~jflegal/EstimatingWithConfidence.pdf)

[^Flegal2012]: Flegal JM. (2012) Applicability of subsampling bootstrap methods in Markov chain Monte Carlo.            Monte Carlo and Quasi-Monte Carlo Methods 2010. pp. 363-72.            doi: [10.1007/978-3-642-27440-4_18](https://doi.org/10.1007/978-3-642-27440-4_18)
