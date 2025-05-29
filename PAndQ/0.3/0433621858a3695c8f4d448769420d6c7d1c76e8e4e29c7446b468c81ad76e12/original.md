```
interpretations(valuations, p)
interpretations(p)
```

Return an `Array{Bool}` given by [`interpret`](@ref)ing `p` with each of the [`valuations`](@ref).

# Examples

```jldoctest
julia> collect(interpretations(⊤))
0-dimensional Array{Bool, 0}:
1

julia> @atomize collect(interpretations(p))
2-element Vector{Bool}:
 1
 0

julia> @atomize collect(interpretations(p ∧ q))
2×2 Matrix{Bool}:
 1  0
 0  0
```
