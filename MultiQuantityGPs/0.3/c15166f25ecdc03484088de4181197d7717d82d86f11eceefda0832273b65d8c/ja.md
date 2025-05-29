```julia
fullCov(
    bm::MultiQuantityGPs.MQGP,
    X::AbstractArray{Tuple{Vector{Float64}, Int64}}
) -> Any

```

信念モデルの完全な共分散行列を返します。
