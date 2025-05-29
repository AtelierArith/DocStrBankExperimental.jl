```
fit_quantile(::Type{<:Stable}, x::AbstractArray{<:Real})
```

McCullochの分位数法を用いて[`Stable`](@ref)分布の推定値を計算します。結果は分布のタイプ0パラメータを含むタプルです。
