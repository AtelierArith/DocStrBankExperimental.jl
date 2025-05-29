```
chi2(res::AbstractVector{OpticalResidual{T, U}} [,
    fit::LeastSquaresFit{T}]) where {T <: Real, U <: Number}
```

`res`のカイ二乗を返します。

$$
\chi^2 = \sum_{i=1}^m w_i \xi_i^2,
$$

ここで、$\xi_i$は統計的重み$w_i$を持つi番目の光学残差です。`fit`が指定されている場合、`fit.x`で残差を評価します。
