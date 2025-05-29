```julia
vmedian!(A; dims)
```

Compute the median of all elements in `A`, optionally over dimensions specified by `dims`. As `Statistics.median!`, but slightly vectorized and supporting the `dims` keyword.

Be aware that, like `Statistics.median!`, this function modifies `A`, sorting or partially sorting the contents thereof (specifically, along the dimensions specified by `dims`, using either `quicksort!` or `quickselect!` around the median depending on the size of the array). Do not use this function if you do not want the contents of `A` to be rearranged.

If reducing over multiple `dims`, these dimensions must be contiguous (i.e. `dims=(2,3)` but not `dims=(1,3)`). Note also that specifying `dims` other than `:` creates `view`s, with some nonzero performance cost.

## Examples

```julia
julia> using VectorizedStatistics

julia> A = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

 julia> vmedian!(A, dims=1)
 1×3 Matrix{Float64}:
  4.0  5.0  6.0

 julia> vmedian!(A, dims=2)
 3×1 Matrix{Float64}:
  2.0
  5.0
  8.0

 julia> vmedian!(A)
 5.0

 julia> A # Note that the array has been sorted
3×3 Matrix{Int64}:
 1  4  7
 2  5  8
 3  6  9
```
