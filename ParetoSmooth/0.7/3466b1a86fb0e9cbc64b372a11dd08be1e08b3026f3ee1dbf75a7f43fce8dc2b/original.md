```
loo_from_psis(
    log_likelihood::AbstractArray{<:Real}, psis_object::Psis; 
    chain_index::Vector{<:Integer}
)
```

Use a precalculated `Psis` object to estimate the leave-one-out cross validation score.

# Arguments

  * `log_likelihood::Array`: A matrix or 3d array of log-likelihood values indexed as

`[data, step, chain]`. The chain argument can be left off if `chain_index` is provided or if all posterior samples were drawn from a single chain.

  * `psis_object`: A precomputed `Psis` object used to estimate the LOO-CV score.
  * `chain_index::Vector{Int}`: An optional vector of integers specifying which chain each step

belongs to. For instance, `chain_index[step]` should return `2` if `log_likelihood[:, step]` belongs to the second chain.

See also: [`psis`](@ref), [`loo`](@ref), [`PsisLoo`](@ref).
