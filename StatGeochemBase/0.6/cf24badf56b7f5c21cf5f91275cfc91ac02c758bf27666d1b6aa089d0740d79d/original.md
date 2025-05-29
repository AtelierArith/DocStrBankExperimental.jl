```julia
zq = linterp1(x, y, z::AbstractMatrix, xq::Number, yq::Number; extrapolate=:Bilinear)
```

Simple linear interpolation in one dimension. Given vectors of knots `x` and `y` and a matrix of values `z`, find the corresponding `z` values at position `xq`,`yq`.

Knot vectors `x` and `y` must be sorted in increasing order, and must match z in dimension, such that `eachindex(x) == axes(z,2)` and `eachindex(y) == axes(z,1)`

If the optional keyword argument `extrapolate` is set to `:Bilinear` (default), out-of-bounds `xq`,`yq` pairs will be extrapolated (or interpolated) linearly in `x`  and then linearly in `y` (yielding a quadratic result as a whole), based on the  closest four z values. Otherwise, if `extrapolate` is set to a `Number`  (e.g., `0`, or `NaN`), that number will be used instead.

### Examples

```julia
julia> x = 1:3
 1:3

julia> y = 1:4
 1:4

julia> z = y*x'
4×3 Matrix{Int64}:
 1  2   3
 2  4   6
 3  6   9
 4  8  12

julia> linterp2(x,y,z,1.5,1.5)
 2.25

julia> linterp2(x,y,z,2.5,3.5)
 8.75

julia> linterp2(x,y,z,1,-10,extrapolate=:Bilinear)
 -10.0

julia> linterp2(x,y,z,2,-10,extrapolate=:Bilinear)
 -20.0
```
