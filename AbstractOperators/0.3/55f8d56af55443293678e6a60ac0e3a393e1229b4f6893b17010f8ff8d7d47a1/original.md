`ZeroPad([domainType::Type,] dim_in::Tuple, zp::Tuple)`

`ZeroPad(x::AbstractArray, zp::Tuple)`

Create a `LinearOperator` which, when multiplied to an array `x` of size `dim_in`, returns an expanded array `y` of size `dim_in .+ zp` where `y[1:dim_in[1], 1:dim_in[2] ... ] = x` and zero elsewhere.  

```julia
julia> Z = ZeroPad((2,2),(0,2))
[I;0]  ℝ^(2, 2) -> ℝ^(2, 4)

julia> Z*ones(2,2)
2×4 Array{Float64,2}:
 1.0  1.0  0.0  0.0
 1.0  1.0  0.0  0.0

```
