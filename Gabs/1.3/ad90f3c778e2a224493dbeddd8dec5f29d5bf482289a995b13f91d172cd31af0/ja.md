```
thermalstate([Tm=Vector{Float64}, Tc=Matrix{Float64},] basis::SymplecticBasis, photons<:Int)
```

熱平衡にあるガウス状態で、熱状態として知られています。シンプレクティック表現は `basis` によって定義されます。状態の平均光子数は `photons` で与えられます。

## 熱状態の数学的記述

熱状態 `|n̄⟩` は、`n̄` が平均光子数であるとき、ゼロ平均ベクトルと共分散行列 `ħ(n̄+1/2)I` によって特徴付けられます。

## 例

```jldoctest
julia> thermalstate(QuadPairBasis(1), 4)
GaussianState for 1 mode.
  symplectic basis: QuadPairBasis
mean: 2-element Vector{Float64}:
 0.0
 0.0
covariance: 2×2 Matrix{Float64}:
 9.0  0.0
 0.0  9.0
```
