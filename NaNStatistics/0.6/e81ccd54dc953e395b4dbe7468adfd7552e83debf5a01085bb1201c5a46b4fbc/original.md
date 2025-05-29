```julia
nanquantile!(A, q; dims)
```

Compute the `q`th quantile (where `q ∈ [0,1]`) of all elements in `A`, ignoring `NaN`s, optionally over dimensions specified by `dims`.

Similar to `StatsBase.quantile!`, but ignoring `NaN`s, and supporting the `dims` keyword.

Be aware that, like `StatsBase.quantile!`, this function modifies `A`, sorting or partially sorting the contents thereof (specifically, along the dimensions specified by `dims`, using either `quicksort!` or `quickselect!` depending on the size of the array). Do not use this function if you do not want the contents of `A` to be rearranged.

Reduction over multiple `dims` is not officially supported, though does work (in generally suboptimal time) as long as the dimensions being reduced over are all contiguous.

## Examples

```julia
julia> using NaNStatistics

julia> A = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

 julia> nanquantile!(A, 0.5, dims=1)
 1×3 Matrix{Float64}:
  4.0  5.0  6.0

 julia> nanquantile!(A, 0.5, dims=2)
 3×1 Matrix{Float64}:
  2.0
  5.0
  8.0

 julia> nanquantile!(A, 0.5)
 5.0

 julia> A # Note that the array has been sorted
3×3 Matrix{Int64}:
 1  4  7
 2  5  8
 3  6  9
```
