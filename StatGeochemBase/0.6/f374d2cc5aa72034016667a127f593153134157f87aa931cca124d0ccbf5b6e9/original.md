```julia
yq = linterp1s(x::AbstractArray, y::AbstractArray, xq; extrapolate=:Linear)
```

As as `linterp1` (simple linear interpolation in one dimension), but will sort the knots `x` and values `y` pairwise if `x` if not already sorted in increasing order.

### Examples

```julia
julia> linterp1s(10:-1:1, 1:10, 5.5)
5.5

julia> linterp1s(10:-1:1, 1:10, 0.5:10.5)
11-element Vector{Float64}:
 10.5
  9.5
  8.5
  7.5
  6.5
  5.5
  4.5
  3.5
  2.5
  1.5
  0.5
```
