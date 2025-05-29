```
vacuumstate([Tm=Vector{Float64}, Tc=Matrix{Float64}], basis::SymplecticBasis)
```

光子がゼロのガウス状態は、真空状態として知られています。シンプレクティック表現は `basis` によって定義されます。

## 真空状態の数学的説明

真空状態 `|0⟩` は、ゼロ平均ベクトルと共分散行列 `(ħ/2)I` によって特徴付けられます。

## 例

```jldoctest
julia> vacuumstate(QuadPairBasis(1))
GaussianState for 1 mode.
  symplectic basis: QuadPairBasis
mean: 2-element Vector{Float64}:
 0.0
 0.0
covariance: 2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
```
