```
phaseshift([Tm=Vector{Float64}, Ts=Matrix{Float64}], basis::SymplecticBasis, theta<:Real)
phaseshift([Tm=Vector{Float64}, Ts=Matrix{Float64}], basis::SymplecticBasis, theta<:Real, noise::Ts)
```

与えられたガウスモードの位相を `theta` だけ回転させるガウス演算子で、位相シフト演算子として機能します。シンプレクティック表現は `basis` によって与えられます。ノイズは `noise` を使って操作に追加できます。

## 位相シフト演算子の数学的説明

位相シフト演算子は、操作 `U(θ) = exp(-iθâᵗâ)` によって定義され、ここで `θ` は位相パラメータであり、`âᵗ` と `â` はそれぞれ昇降演算子です。演算子 `U(θ)` は、ゼロ変位ベクトルとシンプレクティック行列 `[cos(θ) sin(θ); -sin(θ) cos(θ)]` によって特徴付けられます。

## 例

```jldoctest
julia> phaseshift(QuadPairBasis(1), 3pi/4)
GaussianUnitary for 1 mode.
  symplectic basis: QuadPairBasis
displacement: 2-element Vector{Float64}:
 0.0
 0.0
symplectic: 2×2 Matrix{Float64}:
 -0.707107   0.707107
 -0.707107  -0.707107
```
