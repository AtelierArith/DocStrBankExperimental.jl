```
adolc_format_to_seed_space(partials::Vector{Vector{I_1}}, seed_idxs::Vector{I_2}) where {I_1 <: Integer, I_2 <: Integer}
adolc_format_to_seed_space(partials::Vector{Vector{I}}) where I <: Integer
```

Same as [`partial_format_to_seed_space`](@ref) but with [ADOLC-Format](@ref).

# Examples

```jldoctest

partials = [[3, 2], [2, 2]]
seed_idxs = seed_idxs_adolc_format(partials)
adolc_format_to_seed_space(partials, seed_idxs)

# output

2-element Vector{Vector{Int64}}:
 [2, 1]
 [1, 1]
```

Without `seed_idxs`

```jldoctest

partials = [[3, 2], [2, 2]]
seed_idxs = seed_idxs_adolc_format(partials)
adolc_format_to_seed_space(partials, seed_idxs)

# output

2-element Vector{Vector{Int64}}:
 [2, 1]
 [1, 1]
```
