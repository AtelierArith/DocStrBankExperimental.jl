```
nrms(res::AbstractVector{OpticalResidual{T, U}} [,
    fit::LeastSquaresFit{T}]) where {T <: Real, U <: Number}
```

`res`の正規化された二乗平均平方根誤差を返します。`fit`が指定されている場合、`fit.x`で残差を評価します。

[`chi2`](@ref)および[`nms`](@ref)も参照してください。
