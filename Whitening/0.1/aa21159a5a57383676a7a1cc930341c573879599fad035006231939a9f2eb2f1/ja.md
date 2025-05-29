```
`GeneralizedPCA(X::AbstractMatrix{T};
               num_components::Union{Int, Nothing}=nothing,
               vmin::Union{T, Nothing}=nothing,
               rtol::Union{T, Nothing}=nothing) where {T<:Base.IEEEFloat}`

`q × n` 行列から一般化PCA変換器を構築します。各行は `n` 次元の確率変数のサンプルです。
```
