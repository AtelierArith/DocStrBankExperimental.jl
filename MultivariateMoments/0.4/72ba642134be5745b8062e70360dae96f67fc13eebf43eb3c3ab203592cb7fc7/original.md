```
mutable struct FixedRanks <: RankCheck
    r::Vector{Int}
    current::Int
end
```

The `i`th rank is hardcoded to `r[i]`, independently of the singular values. The field `current` indicates how many ranks have already been asked. When `current` is `length(r)`, no rank can be asked anymore.

## Example

```jldoctest
julia> check = FixedRanks([2, 3])
FixedRanks([2, 3], 0)

julia> rank_from_singular_values([1, 1e-1, 5e-5, 1e-5, 5e-6], check)
2

julia> rank_from_singular_values([1, 1e-1, 5e-2, 1e-5, 5e-6], check)
3
```
