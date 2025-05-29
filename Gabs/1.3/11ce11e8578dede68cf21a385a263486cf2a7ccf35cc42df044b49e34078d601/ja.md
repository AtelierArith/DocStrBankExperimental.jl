```
beamsplitter([Tm=Vector{Float64}, Ts=Matrix{Float64}], basis::SymplecticBasis, transmit<:Real)
beamsplitter([Tm=Vector{Float64}, Ts=Matrix{Float64}], basis::SymplecticBasis, transmit<:Real, noise::Ts)
```

二モードガウス状態のビームスプリッタ変換として機能するガウス演算子で、ビームスプリッタ演算子として知られています。シンプレクティック表現は `basis` によって与えられます。演算子の透過率は `transmit` によって与えられます。ノイズは `noise` を使って操作に追加できます。

## ビームスプリッタ演算子の数学的説明

ビームスプリッタ演算子 `B(τ)` は、操作 `B(τ) = exp(θ(âᵗb̂ - âb̂ᵗ))` によって定義され、ここで `θ` は `τ = cos²θ` によって定義され、`â` と `b̂` はそれぞれ二つのモードの消滅演算子です。演算子 `B(τ)` は、ゼロ変位ベクトルとシンプレクティック行列 `[√τI √(1-τ)I; -√(1-τ)I √τI]` によって特徴付けられます。

## 例

```jldoctest
julia> beamsplitter(QuadPairBasis(2), 0.75)
GaussianUnitary for 2 modes.
  symplectic basis: QuadPairBasis
displacement: 4-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
symplectic: 4×4 Matrix{Float64}:
  0.5        0.0       0.866025  0.0
  0.0        0.5       0.0       0.866025
 -0.866025   0.0       0.5       0.0
  0.0       -0.866025  0.0       0.5
```
