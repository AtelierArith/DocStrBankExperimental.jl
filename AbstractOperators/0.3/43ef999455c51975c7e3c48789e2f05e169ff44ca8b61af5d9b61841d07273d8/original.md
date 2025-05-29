`GetIndex([domainType=Float64::Type,] dim_in::Tuple, idx...)`

`GetIndex(x::AbstractArray, idx::Tuple)`

Creates a `LinearOperator` which, when multiplied with `x`, returns `x[idx]`.

```julia
julia> x = collect(linspace(1,10,10));

julia> G = GetIndex(Float64,(10,), 1:3)
↓  ℝ^10 -> ℝ^3 

julia> G*x
3-element Array{Float64,1}:
 1.0
 2.0
 3.0

julia> GetIndex(randn(10,20,30),(1:2,1:4))
↓  ℝ^(10, 20, 30) -> ℝ^(2, 4)

```
