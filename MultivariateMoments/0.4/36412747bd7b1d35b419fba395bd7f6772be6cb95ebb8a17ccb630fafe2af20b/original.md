```
struct LargestDifferentialRank <: RankCheck
end
```

The rank is the number of singular values until the singular value that has the largest ratio with the next singular value.

## Example

It is sometimes difficult to figure out the tolerance to use in [`DifferentialRankTol`](@ref). For instance, choosing `1e-2` will consider `1e-2`, `5e-2` and `1e-3` in the example below as not part of the rank while `LargestDifferentialRank` would include them because there is a largest gap later.

```jldoctest
julia> rank_from_singular_values([1, 1e-2, 5e-2, 1e-3, 1e-6, 5e-7], DifferentialRankTol(1e-2))
1

julia> rank_from_singular_values([1, 1e-2, 5e-2, 1e-3, 1e-6, 5e-7], LargestDifferentialRank())
4
```
