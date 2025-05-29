```
mlr_bands(y::Array{T}; n::Int64=10, se::T=2.0)::Matrix{Float64} where {T<:Real}
```

移動線形回帰バンド

*出力:*

列 1: 下限

列 2: 回帰推定

列 3: 上限
