`IDFT([domainType=Float64::Type,] dim_in::Tuple [,dims])`

`IDFT(dim_in...)`

`IDFT(x::AbstractArray [,dims])`

Creates a `LinearOperator` which, when multiplied with an array `x::AbstractArray{N}`, returns the `N`-dimensional Inverse Discrete Fourier Transform over dimensions `dims` of `x`.

```julia
julia> IDFT(Complex{Float64},(10,10))
ℱ⁻¹  ℂ^(10, 10) -> ℂ^(10, 10)

julia> IDFT(10,10)
ℱ⁻¹ ℝ^(10, 10) -> ℂ^(10, 10)

julia> A = IDFT(ones(3))
ℱ⁻¹  ℝ^3 -> ℂ^3

julia> A*ones(3)
3-element Array{Complex{Float64},1}:
 1.0+0.0im
 0.0+0.0im
 0.0+0.0im
```
