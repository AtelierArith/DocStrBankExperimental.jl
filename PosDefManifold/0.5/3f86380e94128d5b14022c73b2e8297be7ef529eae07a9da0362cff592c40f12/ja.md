```julia
    (1) distance(metric::Metric, P::ℍ{T}) where T<:RealOrComplex
    (2) distance(metric::Metric, P::ℍ{T}, Q::ℍ{T}) where T<:RealOrComplex
    (3) distance(metric::Metric, D::𝔻{S}) where S<:Real
    (4) distance(metric::Metric, D::𝔻{S}, E::𝔻{S}) where S<:Real
```

(1) 正定値行列 $P$ と単位行列との間の *距離* $δ(P, I)$ を返します。

(2) 正定値行列 $P$ と $Q$ との間の *距離* $δ(P, Q)$ を返します。

(3) と (4) は、それぞれ実数の正定値 `Diagonal` 行列に対する (1) と (2) の特化したメソッドです。

これは [`distanceSqr`](@ref) の平方根であり、そこでの同じ構文で呼び出されます。

**関連情報**: [`distanceMat`](@ref).
