```
coherentstate([Tm=Vector{Float64}, Tc=Matrix{Float64},] basis::SymplecticBasis, alpha<:Number)
```

単色の電磁場の量子アナログであるガウス状態、すなわちコヒーレント状態。シンプレクティック表現は `basis` によって定義される。状態の複素振幅は `alpha` で与えられる。

## コヒーレント状態の数学的記述

コヒーレント状態 `|α⟩` は、`α` が複素振幅であるとき、平均ベクトル `√2ħ [real(α), imag(α)]` と共分散行列 `(ħ/2)I` によって特徴付けられる。

## 例

```jldoctest
julia> coherentstate(QuadPairBasis(1), 1.0+im)
GaussianState for 1 mode.
  symplectic basis: QuadPairBasis
mean: 2-element Vector{Float64}:
 2.0
 2.0
covariance: 2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
```
