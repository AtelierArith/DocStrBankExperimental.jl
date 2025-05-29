```julia
compute_model_probs(
    chn::AbstractMatrix
) -> OrderedCollections.OrderedDict{K, Float64} where K<:(Vector{T} where T<:Integer)
compute_model_probs(
    chn::AbstractMatrix,
    add_missing_models::Bool
) -> OrderedCollections.OrderedDict{K, Float64} where K<:(Vector{T} where T<:Integer)

```

各パーティションの事後確率を計算します。
