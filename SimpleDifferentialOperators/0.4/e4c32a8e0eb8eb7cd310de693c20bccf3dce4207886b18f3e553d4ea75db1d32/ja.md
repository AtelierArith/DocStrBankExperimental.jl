```
ExtensionDifferentialOperator(x̄, method::DifferenceMethod)
```

`length(x̄)` 行 `length(x̄) + 2` 列の離散化された微分演算子を返します。最初と最後の列は、境界条件なしで `method` で指定された有限差分法を使用して、`x̄[1]` と `x̄[end]` の直前のゴーストノードに適用されます。

# 例

```jldoctest; setup = :(using SimpleDifferentialOperators)
julia> x̄ = 0:5
0:5

julia> ExtensionDifferentialOperator(x̄, BackwardFirstDifference())
4×6 SparseArrays.SparseMatrixCSC{Float64,Int64} with 11 stored entries:
  [1, 1]  =  -1.0
  [1, 2]  =  1.0
  [2, 2]  =  -1.0
  [1, 3]  =  0.0
  [2, 3]  =  1.0
  [3, 3]  =  -1.0
  [2, 4]  =  0.0
  [3, 4]  =  1.0
  [4, 4]  =  -1.0
  [3, 5]  =  0.0
  [4, 5]  =  1.0

julia> ExtensionDifferentialOperator(x̄, ForwardFirstDifference())
4×6 SparseArrays.SparseMatrixCSC{Float64,Int64} with 11 stored entries:
  [1, 2]  =  -1.0
  [2, 2]  =  0.0
  [1, 3]  =  1.0
  [2, 3]  =  -1.0
  [3, 3]  =  0.0
  [2, 4]  =  1.0
  [3, 4]  =  -1.0
  [4, 4]  =  0.0
  [3, 5]  =  1.0
  [4, 5]  =  -1.0
  [4, 6]  =  1.0

julia> ExtensionDifferentialOperator(x̄, CentralSecondDifference())
4×6 SparseArrays.SparseMatrixCSC{Float64,Int64} with 12 stored entries:
  [1, 1]  =  1.0
  [1, 2]  =  -2.0
  [2, 2]  =  1.0
  [1, 3]  =  1.0
  [2, 3]  =  -2.0
  [3, 3]  =  1.0
  [2, 4]  =  1.0
  [3, 4]  =  -2.0
  [4, 4]  =  1.0
  [3, 5]  =  1.0
  [4, 5]  =  -2.0
  [4, 6]  =  1.0
```
