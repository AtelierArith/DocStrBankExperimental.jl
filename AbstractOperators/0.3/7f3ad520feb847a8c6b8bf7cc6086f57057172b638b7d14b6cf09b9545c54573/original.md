`Variation([domainType=Float64::Type,] dim_in::Tuple)`

`Variation(dims...)`

`Variation(x::AbstractArray)`

Creates a `LinearOperator` which, when multiplied with an array `x::AbstractArray{N}`, returns a matrix with its `i`th column consisting of the vectorized discretized gradient over the `i`th `direction obtained using forward finite differences. 

```julia
julia> Variation(Float64,(10,2))
Ʋ  ℝ^(10, 2) -> ℝ^(20, 2)

julia> Variation(2,2,2)
Ʋ  ℝ^(2, 2, 2) -> ℝ^(8, 3)

julia> Variation(ones(2,2))*[1. 2.; 1. 2.]
4×2 Array{Float64,2}:
 0.0  1.0
 0.0  1.0
 0.0  1.0
 0.0  1.0

```
