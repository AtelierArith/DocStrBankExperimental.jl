```julia
vquantile!(A, q; dims)
```

Compute the `q`th quantile (where `q ∈ [0,1]`) of all elements in `A`, optionally over dimensions specified by `dims`.

Similar to `StatsBase.quantile!`, but slightly vectorized, and supporting the `dims` keyword.

Be aware that, like `StatsBase.quantile!`, this function modifies `A`, sorting or partially sorting the contents thereof (specifically, along the dimensions specified by `dims`, using either `quicksort!` or `quickselect!` depending on the size of the array). Do not use this function if you do not want the contents of `A` to be rearranged.

If reducing over multiple `dims`, these dimensions must be contiguous (i.e. `dims=(2,3)` but not `dims=(1,3)`). Note also that specifying `dims` other than `:` creates `view`s, with some nonzero performance cost.

## Examples

```julia
julia> using VectorizedStatistics

julia> A = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

 julia> vquantile!(A, 0.5, dims=1)
 1×3 Matrix{Float64}:
  4.0  5.0  6.0

 julia> vquantile!(A, 0.5, dims=2)
 3×1 Matrix{Float64}:
  2.0
  5.0
  8.0

 julia> vquantile!(A, 0.5)
 5.0

 julia> A # Note that the array has been sorted
3×3 Matrix{Int64}:
 1  4  7
 2  5  8
 3  6  9
```
