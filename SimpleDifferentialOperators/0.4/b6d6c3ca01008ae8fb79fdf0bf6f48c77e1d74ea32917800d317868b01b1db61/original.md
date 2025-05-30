```
DifferentialOperator(x̄, bc::Tuple{Mixed, Mixed}, method::DifferenceMethod)
```

Returns a discretized differential operator of `length(x̄)` by `length(x̄)` matrix under mixed boundary conditions from `bc` using finite difference method specified by `method`.

# Examples

```jldoctest; setup = :(using SimpleDifferentialOperators)
julia> x̄ = 0:5
0:5

julia> DifferentialOperator(x̄, (Mixed(1.0), Mixed(1.0)), BackwardFirstDifference())
4×4 LinearAlgebra.Tridiagonal{Float64,Array{Float64,1}}:
 -1.0   0.0    ⋅    ⋅
 -1.0   1.0   0.0   ⋅
   ⋅   -1.0   1.0  0.0
   ⋅     ⋅   -1.0  1.0

julia> DifferentialOperator(x̄, (Mixed(1.0), Mixed(1.0)), ForwardFirstDifference())
4×4 LinearAlgebra.Tridiagonal{Float64,Array{Float64,1}}:
 -1.0   1.0    ⋅     ⋅
  0.0  -1.0   1.0    ⋅
   ⋅    0.0  -1.0   1.0
   ⋅     ⋅    0.0  -1.0

julia> DifferentialOperator(x̄, (Mixed(1.0), Mixed(1.0)), CentralSecondDifference())
4×4 LinearAlgebra.Tridiagonal{Float64,Array{Float64,1}}:
 0.0   1.0    ⋅     ⋅
 1.0  -2.0   1.0    ⋅
  ⋅    1.0  -2.0   1.0
  ⋅     ⋅    1.0  -2.0
```
