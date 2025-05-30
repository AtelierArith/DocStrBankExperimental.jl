```
L₁₋bc(x̄, bc::Tuple{BoundaryCondition, BoundaryCondition})
```

`bc`で指定された境界条件の下で後方差分を使用して、`length(x̄)` x `length(x̄)` 行列の離散化された一次微分演算子を返します。

`bc`の最初の要素は下限に適用され、2番目の要素は上限に適用されます。

# 例

```jldoctest; setup = :(using SimpleDifferentialOperators)
julia> x̄ = 0:5
0:5

julia> L₁₋bc(x̄, (Reflecting(), Reflecting()))
4×4 LinearAlgebra.Tridiagonal{Float64,Array{Float64,1}}:
  0.0   0.0    ⋅    ⋅
 -1.0   1.0   0.0   ⋅
   ⋅   -1.0   1.0  0.0
   ⋅     ⋅   -1.0  1.0
```
