```julia
mergeloc(
    estset::MomentMatching.EstimationSetup,
    results::Array{T<:MomentMatching.EstimationResult, 1};
    saving,
    filename_suffix
) -> MomentMatching.EstimationResult{S, T} where {S<:AbstractFloat, Int64<:T<:Integer}

```

異なるローカル推定からの結果をマージします。aux、presh、pmm、および最初の結果からのグローバル結果を使用します。
