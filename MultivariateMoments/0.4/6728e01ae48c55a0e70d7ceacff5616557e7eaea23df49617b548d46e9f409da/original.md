```
struct AbsoluteRankTol{T} <: RankCheck
    tol::T
end
```

The rank is the number of singular values that are strictly larger than `tol`.

## Example

```jldoctest
julia> rank_from_singular_values([1, 1e-1, 5e-2, 1e-5, 5e-6], AbsoluteRankTol(1e-4))
3
```
