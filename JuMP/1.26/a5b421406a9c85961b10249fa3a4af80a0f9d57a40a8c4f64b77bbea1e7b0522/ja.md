```
reshape_vector(vectorized_form::Vector, shape::AbstractShape)
```

ベクトル化された形式 `vectorized_form` に与えられた元の形 `shape` のオブジェクトを返します。

## 例

ベクトル化された形式 `[1, 2, 3]` の [`SymmetricMatrixShape`](@ref) が与えられた場合、次のコードは行列 `Symmetric(Matrix[1 2; 2 3])` を返します：

```jldoctest
julia> reshape_vector([1, 2, 3], SymmetricMatrixShape(2))
2×2 LinearAlgebra.Symmetric{Int64, Matrix{Int64}}:
 1  2
 2  3
```
