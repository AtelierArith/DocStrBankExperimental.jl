```
blockpushfirst!(dest::BlockVector, blocks...) -> dest
```

Push `blocks` to the beginning of `dest`.  See also [`blockpush!`](@ref).

This function avoids copying the elements of the `blocks` when these blocks are compatible with `dest`.  Importantly, this means that mutating `blocks` afterwards alters the items in `dest` and it may even break the invariance of `dest` if the length of `blocks` are changed.

# Examples

```jldoctest
julia> using BlockArrays

julia> blockpushfirst!(mortar([[1], [2, 3]]), [4, 5], [6])
4-blocked 6-element BlockVector{Int64}:
 4
 5
 ─
 6
 ─
 1
 ─
 2
 3
```
