```julia
yq = linterp1(x::AbstractArray, y::AbstractArray, xq; extrapolate=:Linear)
```

Simple linear interpolation in one dimension. Given a vector of knots `x` and values `y`, find the corresponding `y` values at position(s) `xq`.

Knots `x` must be sorted in increasing order.

If the optional keyword argument `extrapolate` is set to `:Linear` (default), `xq` values outside the range of `x` will be extrapolated using a linear extrapolation of the closest two `x`-`y` pairs. Otherwise, if `extrapolate` is set to a `Number` (e.g., `0`, or `NaN`), that number will be used instead.

### Examples

```julia
julia> linterp1(1:10, 1:10, 5.5)
5.5

julia> linterp1(1:10, 1:10, 0.5:10.5)
11-element Vector{Float64}:
  0.5
  1.5
  2.5
  3.5
  4.5
  5.5
  6.5
  7.5
  8.5
  9.5
 10.5
```
