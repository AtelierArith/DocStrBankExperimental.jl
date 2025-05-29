```
nms(res::AbstractVector{OpticalResidual{T, U}} [,
    fit::LeastSquaresFit{T}]) where {T <: Real, U <: Number}
```

`res`の正規化平均二乗誤差を返します。`fit`が指定されている場合、`fit.x`で残差を評価します。

[`chi2`](@ref)を参照してください。
