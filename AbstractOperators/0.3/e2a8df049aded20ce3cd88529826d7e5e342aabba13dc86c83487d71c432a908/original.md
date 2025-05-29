`Eye([domainType=Float64::Type,] dim_in::Tuple)`

`Eye([domainType=Float64::Type,] dims...)`

Create the identity operator.

```julia
julia> op = Eye(Float64,(4,))
I  ℝ^4 -> ℝ^4

julia> op = Eye(2,3,4)
I  ℝ^(2, 3, 4) -> ℝ^(2, 3, 4)

julia> op*ones(2,3,4) == ones(2,3,4)
true

```
