```
function psis_loo(
    log_likelihood::AbstractArray{<:Real} [, args...];
    [, chain_index::Vector{Int}, kwargs...]
) -> PsisLoo
```

Use Pareto-Smoothed Importance Sampling to calculate the leave-one-out cross validation score.

# Arguments

  * `log_likelihood::Array`: A matrix or 3d array of log-likelihood values indexed as

`[data, step, chain]`. The chain argument can be left off if `chain_index` is provided or if all posterior samples were drawn from a single chain.

  * `args...`: Positional arguments to be passed to [`psis`](@ref).
  * `chain_index::Vector{Int}`: An optional vector of integers specifying which chain each step

belongs to. For instance, `chain_index[step]` should return `2` if `log_likelihood[:, step]` belongs to the second chain.

  * `kwargs...`: Keyword arguments to be passed to [`psis`](@ref).

See also: [`psis`](@ref), [`loo`](@ref), [`PsisLoo`](@ref).
