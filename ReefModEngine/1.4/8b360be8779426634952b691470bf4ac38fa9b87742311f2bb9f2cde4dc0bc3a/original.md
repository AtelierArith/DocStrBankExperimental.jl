```
match_id(id::String)::Int64
match_ids(ids::Vector{String})::Vector{Int64}
```

Find matching index position for the given ID(s) according to ReefMod Engine's reef list.

# Note

ReefMod Engine's reef list is in all upper case. The provided IDs are converted to upper case to ensure a match.

# Examples

```julia
julia> reef_ids()
# 3806-element Vector{String}:
#  "10-330"
#  "10-331"
#  ⋮
#  "23-048"
#  "23-049"

julia> match_id("10-330")
#  1

julia> match_id("23-049")
#  3806

julia> match_ids(["23-048", "10-331"])
#  3805
#  2
```
