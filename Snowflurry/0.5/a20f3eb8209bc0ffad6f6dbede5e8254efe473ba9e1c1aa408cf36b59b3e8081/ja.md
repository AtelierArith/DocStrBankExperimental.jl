```
eigen(A::AbstractOperator)
```

演算子 `A` の固有値分解を計算し、`Eigen` 因子分解オブジェクト `F` を返します。固有値は `F.values` にあり、固有ベクトルは行列 `F.vectors` にあります。この行列の各列は固有ベクトルに対応しています。`i` 番目の固有ベクトルは `F.vectors[:, i]` を呼び出すことで抽出されます。

# 例

```jldoctest
julia> X = sigma_x()
(2,2)-element Snowflurry.AntiDiagonalOperator:
Underlying data type: ComplexF64:
    .    1.0 + 0.0im
    1.0 + 0.0im    .

julia> F = eigen(X);

julia> eigenvalues = F.values
2-element Vector{Float64}:
 -1.0
  1.0

julia> eigenvector_1 = F.vectors[:, 1]
2-element Vector{ComplexF64}:
 -0.7071067811865475 + 0.0im
  0.7071067811865475 + 0.0im
```
