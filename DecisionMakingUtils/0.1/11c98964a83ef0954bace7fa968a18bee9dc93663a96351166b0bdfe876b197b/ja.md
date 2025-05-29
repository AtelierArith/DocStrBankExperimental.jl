```
gaussian_stats([::Type{T},] num_features::Int[, weight])
```

この関数は、ベクトルの平均と分散を追跡するための OnlineStats.KahanVariance オブジェクトを作成します。任意の OnlineStats.Weight を使用できます。整数または浮動小数点数が重みとして与えられた場合、デフォルトは OnlineStats.EqualWeight と OnlineStats.ExponentialWeight です。

関連情報: [`extrema_stats`](@ref), [`LinearNormalization`](@ref)

# 例

```jldoctest
julia> stats = gaussian_stats(Float32, 2, 1e-4)
Group
├─ KahanVariance: n=0 | value=1.0
└─ KahanVariance: n=0 | value=1.0

julia> fit!(stats, [1.0, 2.0])
Group
├─ KahanVariance: n=1 | value=1.0
└─ KahanVariance: n=1 | value=1.0

```
