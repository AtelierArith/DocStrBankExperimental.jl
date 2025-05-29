```
twosqueeze([Tm=Vector{Float64}, Ts=Matrix{Float64}], basis::SymplecticBasis, r<:Real, theta<:Real)
twosqueeze([Tm=Vector{Float64}, Ts=Matrix{Float64}], basis::SymplecticBasis, r<:Real, theta<:Real, noise::Ts)
```

二モード真空状態を二モード圧縮状態に圧縮するガウス演算子で、二モード圧縮演算子として知られています。シンプレクティック表現は `basis` によって与えられます。振幅と位相の圧縮パラメータはそれぞれ `r` と `theta` で与えられます。ノイズは `noise` を使って操作に追加できます。

## 二モード圧縮演算子の数学的説明

二モード圧縮演算子 `S₂(r, θ)` は、操作 `S₂(r, θ)|0⟩ = |r, θ⟩` によって定義され、ここで `r` と `θ` はそれぞれ実数の振幅と位相パラメータです。演算子 `S₂(r, θ)` は、ゼロ変位ベクトルとシンプレクティック行列 `[cosh(r)I -sinh(r)R(θ); -sinh(r)R(θ) cosh(r)I]` によって特徴付けられ、ここで `R(θ)` は回転行列です。

## 例

```jldoctest
julia> twosqueeze(QuadPairBasis(2), 0.25, pi/4)
GaussianUnitary for 2 modes.
  symplectic basis: QuadPairBasis
displacement: 4-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
symplectic: 4×4 Matrix{Float64}:
  1.03141    0.0       -0.178624  -0.178624
  0.0        1.03141   -0.178624   0.178624
 -0.178624  -0.178624   1.03141    0.0
 -0.178624   0.178624   0.0        1.03141
```
