```
struct FixedRank <: RankCheck
    r::Int
end
```

The rank is hardcoded to `r`, independently of the singular values.

## Example

```jldoctest
julia> rank_from_singular_values([1, 1e-1, 5e-2, 1e-5, 5e-6], FixedRank(3))
3
```
