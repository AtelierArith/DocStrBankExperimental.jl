```julia
struct AliasingScalarSampler
```

ユークリッド空間 `x` と確率重み `p_x` からの強度マップのサンプラー。

例

`AliasingScalarSampler(x::Vector{<:Real}, p_x::Vector{<:Real}; SNRfloor::Float64=0.0)`
