`LMatrixOp(domainType=Float64::Type, dim_in::Tuple, b::Union{AbstractVector,AbstractMatrix})`

`LMatrixOp(b::AbstractVector, number_of_rows::Int)`

Creates a `LinearOperator` which, when multiplied with a matrix `X::AbstractMatrix`, returns the product `X*b`.

```julia
julia> op = LMatrixOp(Float64,(3,4),ones(4))
(⋅)b  ℝ^(3, 4) -> ℝ^3 

julia> op = LMatrixOp(ones(4),3)
(⋅)b  ℝ^(3, 4) -> ℝ^3

julia> op*ones(3,4)
3-element Array{Float64,1}:
 4.0
 4.0
 4.0

```
