```
SoftLog(x::Union{T, AbstractVector{T}}; eps::Real=1e-20) where T<:Number
```

自動微分での `NaN` エラーを避けるために `log(x + eps)` を計算します。
