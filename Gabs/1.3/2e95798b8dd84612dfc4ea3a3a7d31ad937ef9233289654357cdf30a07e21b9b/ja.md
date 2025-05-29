```
squeeze([Tm=Vector{Float64}, Ts=Matrix{Float64}], basis::SymplecticBasis, r<:Real, theta<:Real)
squeeze([Tm=Vector{Float64}, Ts=Matrix{Float64}], basis::SymplecticBasis, r<:Real, theta<:Real, noise::Ts)
```

真空状態を圧縮状態に圧縮するガウス演算子で、これを圧縮演算子と呼びます。シンプレクティック表現は `basis` によって与えられます。振幅と位相の圧縮パラメータはそれぞれ `r` と `theta` で与えられます。ノイズは `noise` を使って操作に追加できます。

## 圧縮演算子の数学的説明

圧縮演算子 `S(r, θ)` は、操作 `S(r, θ)|0⟩ = |r, θ⟩` によって定義され、ここで `r` と `θ` はそれぞれ実数の振幅と位相パラメータです。演算子 `S(r, θ)` は、ゼロ変位ベクトルとシンプレクティック行列 `cosh(r)I - sinh(r)R(θ)` によって特徴付けられ、ここで `R(θ)` は回転行列です。

## 例

```jldoctest
julia> squeeze(QuadPairBasis(1), 0.25, pi/4)
GaussianUnitary for 1 mode.
  symplectic basis: QuadPairBasis
displacement: 2-element Vector{Float64}:
 0.0
 0.0
symplectic: 2×2 Matrix{Float64}:
  0.852789  -0.178624
 -0.178624   1.21004
```
