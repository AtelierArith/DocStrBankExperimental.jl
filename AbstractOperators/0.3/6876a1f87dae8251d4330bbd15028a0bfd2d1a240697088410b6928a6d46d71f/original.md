`RDFT([domainType=Float64::Type,] dim_in::Tuple [,dims=1])`

`RDFT(dim_in...)`

`RDFT(x::AbstractArray [,dims=1])`

Creates a `LinearOperator` which, when multiplied with a real array `x`, returns the DFT over the dimension `dims`, exploiting Hermitian symmetry. 

```julia
julia> RDFT(Float64,(10,10))
ℱ  ℝ^(10, 10) -> ℂ^(6, 10)

julia> RDFT((10,10,10),2)
ℱ  ℝ^(10, 10, 10) -> ℂ^(10, 6, 10)

```
