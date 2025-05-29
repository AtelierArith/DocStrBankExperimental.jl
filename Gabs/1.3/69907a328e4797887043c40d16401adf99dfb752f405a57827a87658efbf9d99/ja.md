```
eprstate([Tm=Vector{Float64}, Tc=Matrix{Float64},] basis::SymplecticBasis, r<:Real, theta<:Real)
```

エンタングル状態である二モード圧縮状態、すなわちアインシュタイン-ポドルスキー-ローゼン（EPR）状態です。シンプレクティック表現は `basis` によって定義されます。振幅と位相の圧縮パラメータはそれぞれ `r` と `theta` で与えられます。

## EPR状態の数学的記述

EPR状態 `|r, θ⟩ₑₚᵣ` は、`r` が振幅圧縮パラメータ、`θ` が位相圧縮パラメータであるとき、ゼロ平均ベクトルと共分散行列 `(ħ/2)[cosh(2r)I -sinh(2r)R(θ); -sinh(2r)R(θ) cosh(2r)I]` によって特徴付けられます。ここで `R(θ)` は回転行列です。

## 例

```jldoctest
julia> eprstate(QuadPairBasis(2), 0.5, pi/4)
GaussianState for 2 modes.
  symplectic basis: QuadPairBasis
mean: 4-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
covariance: 4×4 Matrix{Float64}:
  1.54308    0.0       -0.830993  -0.830993
  0.0        1.54308   -0.830993   0.830993
 -0.830993  -0.830993   1.54308    0.0
 -0.830993   0.830993   0.0        1.54308
```
