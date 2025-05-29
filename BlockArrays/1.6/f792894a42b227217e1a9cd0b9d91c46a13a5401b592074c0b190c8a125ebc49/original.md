```
blockpopfirst!(dest::BlockVector) -> block
```

Pop a `block` from the beginning of `dest`.

# Examples

```jldoctest
julia> using BlockArrays

julia> A = mortar([[1], [2, 3]]);

julia> blockpopfirst!(A)
1-element Vector{Int64}:
 1

julia> A
1-blocked 2-element BlockVector{Int64}:
 2
 3
```
