```
struct LeadingRelativeRankTol{T} <: RankCheck
    tol::T
end
```

The rank is the number of singular values that are strictly larger than `tol * maximum(σ)` where `maximum(σ)` is the largest singular value.

## Example

When the matrix is obtained from a homogeneous problem where the scaling is irrelevant, `LeadingRelativeRankTol` may be preferable to [`AbsoluteRankTol`](@ref) as shown below

```jldoctest
julia> rank_from_singular_values(1e6 * [1, 1e-1, 5e-2, 1e-5, 5e-6], AbsoluteRankTol(1e-4))
5

julia> rank_from_singular_values(1e6 * [1, 1e-1, 5e-2, 1e-5, 5e-6], LeadingRelativeRankTol(1e-4))
3
```
