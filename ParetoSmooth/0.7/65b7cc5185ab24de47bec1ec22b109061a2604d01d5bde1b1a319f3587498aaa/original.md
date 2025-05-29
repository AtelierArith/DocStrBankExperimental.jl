```
psis(
    log_ratios::AbstractArray{T<:Real}, 
    r_eff::AbstractVector{T}; 
    source::String="mcmc"    
) -> Psis
```

Implements Pareto-smoothed importance sampling (PSIS).

# Arguments

## Positional Arguments

  * `log_ratios::AbstractArray`: A 2d or 3d array of (unnormalized) importance ratios on the log scale. Indices must be ordered as `[data, step, chain]`. The chain index can be left  off if there is only one chain, or if keyword argument `chain_index` is provided.
  * `r_eff::AbstractVector`: An (optional) vector of relative effective sample sizes used in ESS

calculations. If left empty, calculated automatically using the FFTESS method from InferenceDiagnostics.jl. See `relative_eff` to calculate these values.

## Keyword Arguments

  * `chain_index::Vector{Int}`: An optional vector of integers specifying which chain each step

belongs to. For instance, `chain_index[step]` should return `2` if `log_likelihood[:, step]` belongs to the second chain.

  * `source::String="mcmc"`: A string or symbol describing the source of the sample being  used. If `"mcmc"`, adjusts ESS for autocorrelation. Otherwise, samples are assumed to be  independent. Currently permitted values are ["mcmc", "vi", "other"].
  * `calc_ess::Bool=true`: If `false`, do not calculate ESS diagnostics. Attempting to access ESS diagnostics will return an empty array.
  * `checks::Bool=true`: If `true`, check inputs for possible errors. Disabling will improve  performance slightly.

See also: [`relative_eff`]@ref, [`psis_loo`]@ref, [`psis_ess`]@ref.
