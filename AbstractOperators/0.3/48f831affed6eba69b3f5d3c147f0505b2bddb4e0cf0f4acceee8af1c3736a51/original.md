`IRDFT([domainType=Float64::Type,] dim_in::Tuple, d::Int, [,dims=1])`

`IRDFT(x::AbstractArray, d::Int, [,dims=1])`

Creates a `LinearOperator` which, when multiplied with a complex array `x`, returns the IDFT over the dimension `dims`, exploiting Hermitian symmetry. Like in the function `BASE.irfft`, `d` must satisfy `div(d,2)+1 == size(x,dims)`.

```julia
julia> A = IRDFT(Complex{Float64},(10,),19)
ℱ⁻¹  ℂ^10 -> ℝ^19 

julia> A = IRDFT((5,10,8),19,2)
ℱ⁻¹  ℂ^(5, 10, 8) -> ℝ^(5, 19, 8)

```
