```
blockappend!(dest::BlockVector, sources...) -> dest
```

Append blocks from `sources` to `dest`.  The number of blocks in `dest` are increased by `sum(blocklength, sources)`.

This function avoids copying the elements of the blocks in `sources` when these blocks are compatible with `dest`.  Importantly, this means that mutating `sources` afterwards alters the items in `dest` and it may even break the invariance of `dest` if the length of `sources` are changed.

The blocks in `dest` must not alias with `sources` or components of them. For example, the result of `blockappend!(x, x)` is undefined.

# Examples

```jldoctest
julia> using BlockArrays

julia> blockappend!(mortar([[1], [2, 3]]), mortar([[4, 5]]))
3-blocked 5-element BlockVector{Int64}:
 1
 ─
 2
 3
 ─
 4
 5
```
