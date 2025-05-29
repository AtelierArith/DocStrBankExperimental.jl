```
AffineIntervalMatrix1{T, IT, MT0<:AbstractMatrix{T}, MT1<:AbstractMatrix{T}} <: AbstractIntervalMatrix{IT}
```

行列を表す区間行列

$$
A₀ + λA₁,
$$

ここで、$A₀$ と $A₁$ は実数（または複素数）行列であり、$λ$ は区間です。

### フィールド

  * `A0` – 行列
  * `A1` – 行列
  * `λ`  – 区間

### 例

行列 $I + [1 1; -1 1] * interval(0, 1)$ は次のようになります：

```jldoctest
julia> using LinearAlgebra

julia> P = AffineIntervalMatrix1(Matrix(1.0I, 2, 2), [1 1; -1 1.], interval(0, 1));

julia> P
2×2 AffineIntervalMatrix1{Float64, Interval{Float64}, Matrix{Float64}, Matrix{Float64}}:
  [1.0, 2.0]  [0.0, 1.0]
 [-1.0, 0.0]  [1.0, 2.0]
```
