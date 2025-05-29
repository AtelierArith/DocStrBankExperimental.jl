```
partial_format_to_seed_space(partials::Vector{Vector{I_1}}, seed_idxs::Vector{I_2}) where {I_1 <: Integer, I_2 <: Integer}
partial_format_to_seed_space(partials::Vector{Vector{I}}) where I <: Integer
```

Converts `partials` in [Partial-Format](@ref) to `partials` of the same format but with (possible) reduced number  of derivatives directions. The `seed_idxs` is expected to store the result of [`seed_idxs_partial_format(seed_idxs)`](@ref). Without `seed_idxs` the function first calls [`seed_idxs_partial_format(seed_idxs)`](@ref) to get the indices.

# Examples

```jldoctest

partials = [[0, 1, 1], [0, 2, 0]]
seed_idxs = seed_idxs_partial_format(partials)
partial_format_to_seed_space(partials, seed_idxs)

# output

2-element Vector{Vector{Int64}}:
 [1, 1]
 [2, 0]
```

Without `seed_idxs`

```jldoctest

partials = [[0, 1, 1], [0, 2, 0]]
partial_format_to_seed_space(partials)

# output

2-element Vector{Vector{Int64}}:
 [1, 1]
 [2, 0]
```
