```
function sup_ess(
    weights::AbstractMatrix{T},
    r_eff::AbstractVector{T}
) -> AbstractVector
```

Calculate the supremum-based effective sample size of a PSIS sample, i.e. the inverse of the maximum weight. This measure is more sensitive than the `ess` from `psis_ess`, but also  much more variable. It uses the L-∞ norm.

# Arguments

  * `weights`: A set of importance sampling weights derived from PSIS.
  * `r_eff`: The relative efficiency of the MCMC chains; see also [`relative_eff`]@ref.
