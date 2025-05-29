```
SoftAbs(x::Union{T, AbstractVector{T}}; eps::Real=1e-100) where T<:Number
```

絶対値関数 `abs` の微分可能な近似を `sqrt(abs2(x) + eps)` として計算します。
