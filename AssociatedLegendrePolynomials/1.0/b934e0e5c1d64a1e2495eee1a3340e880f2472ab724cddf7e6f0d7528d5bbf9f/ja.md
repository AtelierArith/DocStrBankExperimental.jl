```
struct LegendreNormCoeff{N<:AbstractLegendreNorm,T<:Real} <: AbstractLegendreNorm
```

正規化のための事前計算された再帰関係係数 `N` と値の型 `T`。

# 例

```jldoctest
julia> LegendreNormCoeff{LegendreSphereNorm,Float64}(1)
LegendreNormCoeff{LegendreSphereNorm,Float64} for lmax = 1, mmax = 1 with coefficients:
    μ: [0.0, 1.22474]
    ν: [1.73205, 2.23607]
    α: [0.0 0.0; 1.73205 0.0]
    β: [0.0 0.0; -0.0 0.0]
```
