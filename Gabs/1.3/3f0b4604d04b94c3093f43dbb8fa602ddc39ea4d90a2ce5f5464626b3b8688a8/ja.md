```
squeezedstate([Tm=Vector{Float64}, Tc=Matrix{Float64},] basis::SymplecticBasis, r<:Real, theta<:Real)
```

位相と振幅に量子不確定性を持つガウス状態で、これを圧縮状態と呼びます。シンプレクティック表現は `basis` によって定義されます。振幅と位相の圧縮パラメータはそれぞれ `r` と `theta` で与えられます。

## 圧縮状態の数学的説明

圧縮状態 `|r, θ⟩` は、`r` が振幅圧縮パラメータ、`θ` が位相圧縮パラメータである状態で、ゼロ平均ベクトルと共分散行列 `(ħ/2) (cosh(2r)I - sinh(2r)R(θ))` によって特徴付けられます。ここで `R(θ)` は回転行列です。

## 例

```jldoctest
julia> squeezedstate(QuadPairBasis(1), 0.5, pi/4)
GaussianState for 1 mode.
  symplectic basis: QuadPairBasis
mean: 2-element Vector{Float64}:
 0.0
 0.0
covariance: 2×2 Matrix{Float64}:
  0.712088  -0.830993
 -0.830993   2.37407
```
