```
AffineIntervalMatrix{T, IT, MT0<:AbstractMatrix{T}, MT<:AbstractMatrix{T}, MTA<:AbstractVector{MT}} <: AbstractIntervalMatrix{IT}
```

行列を表す区間行列

$$
A₀ + λ₁A₁ + λ₂A₂ + … + λₖAₖ,
$$

ここで、$A₀$ および $A₁, …, Aₖ$ は実数（または複素数）行列であり、$λ₁, …, λₖ$ は区間です。

### フィールド

  * `A0` – 行列
  * `A`  – 行列のベクトル
  * `λ`  – 区間のベクトル

### 注意事項

この型は、区間に比例する1つの行列のみを含む [`AffineIntervalMatrix1`](@ref) の一般的なケースです。

### 例

アフィン行列 $I + [1 1; -1 1] * interval(0, 1) + [0 1; 1 0] * interval(2, 3)$ は次のようになります：

```jldoctest
julia> using LinearAlgebra

julia> A0 = Matrix(1.0I, 2, 2);

julia> A1 = [1 1; -1 1.]; A2 = [0 1; 1 0];

julia> λ1 = interval(0, 1); λ2 = interval(2, 3);

julia> P = AffineIntervalMatrix(A0, [A1, A2], [λ1, λ2])
2×2 AffineIntervalMatrix{Float64, Interval{Float64}, Matrix{Float64}, Matrix{Float64}, Vector{Matrix{Float64}}, Vector{Interval{Float64}}}:
 [1.0, 2.0]  [2.0, 4.0]
 [1.0, 3.0]  [1.0, 2.0]
```
