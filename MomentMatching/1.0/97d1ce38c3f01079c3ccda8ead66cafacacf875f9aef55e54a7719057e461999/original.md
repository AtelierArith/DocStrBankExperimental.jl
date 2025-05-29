```julia
mergeloc(
    estset::MomentMatching.EstimationSetup,
    results::Array{T<:MomentMatching.EstimationResult, 1};
    saving,
    filename_suffix
) -> MomentMatching.EstimationResult{S, T} where {S<:AbstractFloat, Int64<:T<:Integer}

```

Merges results from different local estimations. Uses aux, presh, pmm and global results from first result.
