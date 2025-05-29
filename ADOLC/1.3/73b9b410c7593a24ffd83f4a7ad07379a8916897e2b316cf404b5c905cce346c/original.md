```
seed_idxs_adolc_format(partials::Vector{Vector{I}}) where I <: Integer
```

Extracts the actually required derivative directions of `partials` and returns them  ascendet sorted. 

!!! note
    `partials` has to be in [ADOLC-Format](@ref).


# Example

```jldoctest

partials = [[5, 5, 5, 1], [3, 1, 0, 0], [3, 3, 3, 0]]
seed_idxs_adolc_format(partials)

# output

3-element Vector{Int64}:
 1
 3
 5
```
