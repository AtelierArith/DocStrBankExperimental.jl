```
blockpop!(A::BlockVector) -> block
```

Pop a `block` from the end of `dest`.

# Examples

```jldoctest
julia> using BlockArrays

julia> A = mortar([[1], [2, 3]]);

julia> blockpop!(A)
2-element Vector{Int64}:
 2
 3

julia> A
1-blocked 1-element BlockVector{Int64}:
 1
```
