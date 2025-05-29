```
changebasis_R(P::AbstractFunctionSpace, P′::AbstractFunctionSpace)
```

Return a coefficient matrix $A$ which satisfy

$$
B_{(i,p,k)} = \sum_{j}A_{i,j}B_{(j,p',k')}
$$

# Examples

```jldoctest
julia> P = BSplineSpace{2}(knotvector"3 13")
BSplineSpace{2, Int64, KnotVector{Int64}}(KnotVector([1, 1, 1, 3, 4, 4, 4]))

julia> P′ = BSplineSpace{3}(knotvector"4124")
BSplineSpace{3, Int64, KnotVector{Int64}}(KnotVector([1, 1, 1, 1, 2, 3, 3, 4, 4, 4, 4]))

julia> P ⊆ P′
true

julia> changebasis_R(P, P′)
4×7 SparseArrays.SparseMatrixCSC{Float64, Int32} with 13 stored entries:
 1.0  0.666667  0.166667   ⋅         ⋅         ⋅         ⋅
  ⋅   0.333333  0.722222  0.555556  0.111111   ⋅         ⋅
  ⋅    ⋅        0.111111  0.444444  0.888889  0.666667   ⋅
  ⋅    ⋅         ⋅         ⋅         ⋅        0.333333  1.0
```
