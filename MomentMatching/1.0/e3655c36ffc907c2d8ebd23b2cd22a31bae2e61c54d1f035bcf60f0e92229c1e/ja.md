```julia
mergeglo(
    estset::MomentMatching.EstimationSetup,
    results::Array{T<:MomentMatching.EstimationResult, 1};
    saving,
    filename_suffix
) -> MomentMatching.EstimationResult{Float64}

```

異なるグローバル推定からの結果をマージします。最初の結果から aux, presh, pmm を使用します。
