```julia
nanmedian!(A; dims)
```

Compute the median of all elements in `A`, optionally over dimensions specified by `dims`. As `Statistics.median!`, but ignoring `NaN`s and supporting the `dims` keyword.

Be aware that, like `Statistics.median!`, this function modifies `A`, sorting or partially sorting the contents thereof (specifically, along the dimensions specified by `dims`, using either `quicksort!` or `quickselect!` around the median depending on the size of the array). Do not use this function if you do not want the contents of `A` to be rearranged.

Reduction over multiple `dims` is not officially supported, though does work (in generally suboptimal time) as long as the dimensions being reduced over are all contiguous.

Optionally supports the `dim` keyword, which behaves identically to `dims`, but also drops any singleton dimensions that have been reduced over (as is the convention in some other languages).

## Examples

```julia
julia> using NaNStatistics

julia> A = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

 julia> nanmedian!(A, dims=1)
 1×3 Matrix{Float64}:
  4.0  5.0  6.0

 julia> nanmedian!(A, dims=2)
 3×1 Matrix{Float64}:
  2.0
  5.0
  8.0

 julia> nanmedian!(A)
 5.0

 julia> A # Note that the array has been sorted
3×3 Matrix{Int64}:
 1  4  7
 2  5  8
 3  6  9
```
