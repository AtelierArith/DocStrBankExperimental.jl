```julia
mergeglo(
    estset::MomentMatching.EstimationSetup,
    results::Array{T<:MomentMatching.EstimationResult, 1};
    saving,
    filename_suffix
) -> MomentMatching.EstimationResult{Float64}

```

Merges results from different global estimations. Uses aux, presh, pmm from first result.
