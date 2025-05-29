```julia
nancumsum(A; dims)
```

Calculate the sum of an indexable collection `A`, ignoring `NaN`s, optionally along dimensions specified by `dims`.

## Examples

```julia
julia> using NaNStatistics

julia> A = [1 2; 3 4; NaN NaN]
3×2 Matrix{Float64}:
   1.0    2.0
   3.0    4.0
 NaN    NaN

julia> nancumsum(A, dims=1)
3×2 Matrix{Float64}:
 1.0  2.0
 4.0  6.0
 4.0  6.0

julia> nancumsum(vec(A))
6-element Vector{Float64}:
  1.0
  4.0
  4.0
  6.0
 10.0
 10.0
```
