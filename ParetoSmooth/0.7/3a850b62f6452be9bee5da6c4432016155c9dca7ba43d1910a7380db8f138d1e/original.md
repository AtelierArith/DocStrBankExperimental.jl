```
function psis_ess(
    weights::AbstractVector{T<:Real},
    r_eff::AbstractVector{T}
) -> AbstractVector{T}
```

Calculate the (approximate) effective sample size of a PSIS sample, using the correction in Vehtari et al. 2019. This uses the entropy-based definition of ESS, measuring the K-L divergence of the proposal and target distributions.

# Arguments

  * `weights`: A set of normalized importance sampling weights derived from PSIS.
  * `r_eff`: The relative efficiency of the MCMC chains from which PSIS samples were derived.

See `?relative_eff` to calculate `r_eff`.
