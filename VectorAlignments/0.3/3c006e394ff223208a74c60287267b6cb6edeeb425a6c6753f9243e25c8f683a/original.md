Align each of the vectors in the parameter list to the comprehensive SCS for all of the parameter vectors.

# Examples

```jldoctest
julia> align([1,3,5], [1,2,3])
2-element Vector{Any}:
 Any[1, nothing, 3, 5]
 Any[1, 2, 3, nothing]
```

```julia
align(v; norm, cf)

```
