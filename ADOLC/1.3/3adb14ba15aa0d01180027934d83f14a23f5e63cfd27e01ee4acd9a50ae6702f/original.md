```
seed_idxs_partial_format(partials::Vector{Vector{I}}) where I <: Integer
```

Extracts the actually required derivative directions of `partials` and returns them  ascendet sorted. 

!!! note
    `partials` has to be in [Partial-Format](@ref).


# Example

```jldoctest

partials = [[1, 0, 0, 0, 3], [1, 0, 1, 0, 0], [0, 0, 3, 0, 0]]
seed_idxs_partial_format(partials)

# output

3-element Vector{Int64}:
 1
 3
 5
```
