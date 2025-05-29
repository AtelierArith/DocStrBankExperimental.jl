```
struct DifferentialRankTol{T} <: RankCheck
    tol::T
end
```

The rank is the number of singular values before a singular value (not included) is `tol` times the previous one (included).

## Example

It is sometimes difficult to figure out the tolerance to use in [`LeadingRelativeRankTol`](@ref). For instance, choosing `1e-3` will consider `1e-3` in the example below as not part of the rank while `DifferentialRankTol` would include it because it is close to the previous singular value.

```jldoctest
julia> rank_from_singular_values([1, 1e-1, 5e-2, 1e-2, 5e-3, 1e-3, 1e-6, 5e-7], LeadingRelativeRankTol(1e-3))
5

julia> rank_from_singular_values([1, 1e-1, 5e-2, 1e-2, 5e-3, 1e-3, 1e-6, 5e-7], DifferentialRankTol(1e-2))
6
```
