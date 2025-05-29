```julia
compute_model_counts(
    partition_samples::AbstractArray{T<:Integer, 2}
) -> OrderedCollections.OrderedDict{K, Int64} where K<:(Vector{T} where T<:Integer)
compute_model_counts(
    partition_samples::AbstractArray{T<:Integer, 2},
    add_missing_models::Bool
) -> OrderedCollections.OrderedDict{K, Int64} where K<:(Vector{T} where T<:Integer)

```

各パーティションがどれくらい訪問されるかを計算します。
