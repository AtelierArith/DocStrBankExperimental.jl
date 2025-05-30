```
ExtensionDifferentialOperator(x̄, method::DifferenceMethod)
```

Returns a discretized differential operator of `length(x̄)` by `length(x̄) + 2` matrix whose first and last columns are applied to the ghost nodes just before `x̄[1]` and `x̄[end]` respectively under no boundary condition using finite difference method specified by `method`.

# Examples

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
