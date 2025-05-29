```
reshape_set(vectorized_set::MOI.AbstractSet, shape::AbstractShape)
```

与えられたベクトル化形式 `vectorized_form` に対して、元の形 `shape` のセットを返します。

## 例

ベクトル化形式 `[1, 2, 3]` の [`SymmetricMatrixShape`](@ref) が `MOI.PositiveSemidefinieConeTriangle(2)` にある場合、次のコードは元の制約のセット `Symmetric(Matrix[1 2; 2 3]) in PSDCone()` を返します：

```jldoctest
julia> reshape_set(MOI.PositiveSemidefiniteConeTriangle(2), SymmetricMatrixShape(2))
PSDCone()
```
