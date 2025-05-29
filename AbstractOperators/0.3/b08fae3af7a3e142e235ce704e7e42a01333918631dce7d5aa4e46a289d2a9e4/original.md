`DCT([domainType=Float64::Type,] dim_in::Tuple)`

`DCT(dim_in...)`

`DCT(x::AbstractArray)`

Creates a `LinearOperator` which, when multiplied with an array `x::AbstractArray{N}`, returns the `N`-dimensional Inverse Discrete Cosine Transform of `x`. 

```julia
julia> DCT(Complex{Float64},(10,10))
ℱc  ℂ^(10, 10) -> ℂ^(10, 10) 

julia> DCT(10,10)
ℱc  ℝ^(10, 10) -> ℂ^(10, 10) 

julia> A = DCT(ones(3))
ℱc  ℝ^3 -> ℝ^3

julia> A*ones(3)
3-element Array{Float64,1}:
 1.73205
 0.0
 0.0

```
