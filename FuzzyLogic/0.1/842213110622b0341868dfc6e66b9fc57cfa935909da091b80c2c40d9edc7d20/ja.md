```julia
struct GeneralizedBellMF{T<:Real, S<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

一般化ベル会員関数 $\frac{1}{1+\vert\frac{x-c}{a}\vert^{2b}}$。

### フィールド

  * `a::Real`: 曲線の幅、大きいほど広くなる。
  * `b::Real`: 曲線の傾き、大きいほど急になる。
  * `c::Real`: 曲線の中心。

### 例

```julia
mf = GeneralizedBellMF(2, 4, 5)
```
