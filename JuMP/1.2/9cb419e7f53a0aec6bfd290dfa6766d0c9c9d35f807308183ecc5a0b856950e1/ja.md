```
reshape_vector(vectorized_form::Vector, shape::AbstractShape)
```

ベクトル化された形式 `vectorized_form` に基づいて、元の形状 `shape` のオブジェクトを返します。

## 例

ベクトル化された形式 `[1, 2, 3]` の [`SymmetricMatrixShape`](@ref) が与えられた場合、次のコードは行列 `Symmetric(Matrix[1 2; 2 3])` を返します：

```jldoctest; setup = :(using JuMP)
julia> reshape_vector([1, 2, 3], SymmetricMatrixShape(2))
2×2 LinearAlgebra.Symmetric{Int64,Array{Int64,2}}:
 1  2
 2  3
```
