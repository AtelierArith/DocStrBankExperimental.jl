`FiniteDiff([domainType=Float64::Type,] dim_in::Tuple, direction = 1)`

`FiniteDiff(x::AbstractArray, direction = 1)`

Creates a `LinearOperator` which, when multiplied with an array `x::AbstractArray{N}`, returns the discretized gradient over the specified `direction` obtained using forward finite differences. 

```julia
julia> FiniteDiff(Float64,(3,))
δx  ℝ^3 -> ℝ^2

julia> FiniteDiff((3,4),2)
δy  ℝ^(3, 4) -> ℝ^(3, 3)

julia> all(FiniteDiff(ones(2,2,2,3),1)*ones(2,2,2,3) .== 0)
true

```
