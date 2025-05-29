```
displace([Tm=Vector{Float64}, Ts=Matrix{Float64}], basis::SymplecticBasis, alpha<:Number)
displace([Tm=Vector{Float64}, Ts=Matrix{Float64}], basis::SymplecticBasis, alpha<:Number, noise::Ts)
```

真空状態をコヒーレント状態に移動させるガウス演算子で、これを移動演算子と呼びます。シンプレクティック表現は `basis` によって与えられます。複素振幅は `alpha` で与えられます。ノイズは `noise` を使って操作に追加できます。

## 移動演算子の数学的説明

移動演算子 `D(α)` は、操作 `D(α)|0⟩ = |α⟩` によって定義され、ここで `α` は複素振幅です。演算子 `D(α)` は、移動ベクトル `√2ħ [real(α), imag(α)]` とシンプレクティック行列 `I` によって特徴付けられます。

## 例

```jldoctest
julia> displace(QuadPairBasis(1), 1.0+im)
GaussianUnitary for 1 mode.
  symplectic basis: QuadPairBasis
displacement: 2-element Vector{Float64}:
 2.0
 2.0
symplectic: 2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
```
