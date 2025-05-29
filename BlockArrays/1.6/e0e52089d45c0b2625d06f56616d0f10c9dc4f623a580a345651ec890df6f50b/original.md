```
blockpush!(dest::BlockVector, blocks...) -> dest
```

Push `blocks` to the end of `dest`.

This function avoids copying the elements of the `blocks` when these blocks are compatible with `dest`.  Importantly, this means that mutating `blocks` afterwards alters the items in `dest` and it may even break the invariance of `dest` if the length of `blocks` are changed.

# Examples

```jldoctest
julia> using BlockArrays

julia> blockpush!(mortar([[1], [2, 3]]), [4, 5], [6])
4-blocked 6-element BlockVector{Int64}:
 1
 ─
 2
 3
 ─
 4
 5
 ─
 6
```
