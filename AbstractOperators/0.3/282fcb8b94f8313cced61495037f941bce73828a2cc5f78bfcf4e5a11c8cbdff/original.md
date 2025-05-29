`DiagOp(domainType::Type, dim_in::Tuple, d::AbstractArray)`

`DiagOp(d::AbstractArray)`

Creates a `LinearOperator` which, when multiplied with an array `x`, returns the elementwise product `d.*x`.

```julia
julia> D = DiagOp(Float64, (2, 2,), [1. 2.; 3. 4.])
╲  ℝ^(2, 2) -> ℝ^(2, 2)

julia> D*ones(2,2)
2×2 Array{Float64,2}:
 1.0  2.0
 3.0  4.0

```
