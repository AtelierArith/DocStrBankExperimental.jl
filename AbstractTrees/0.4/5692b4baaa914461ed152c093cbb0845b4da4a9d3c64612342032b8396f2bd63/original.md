```
ChildIndexing(::Type{N})
ChildIndexing(node)
```

A trait indicating whether the tree node `n` has children (as returned by [`children`](@ref)) which can be indexed using 1-based indexing. Options are either [`NonIndexedChildren`](@ref) (default) or [`IndexedChildren`](@ref).

To declare that the tree `TreeType` supports one-based indexing on the children, define

```julia
AbstractTrees.ChildIndexing(::Type{<:TreeType}) = AbstractTrees.IndexedChildren()
```

If a node has the `IndexedChildren()` so must all connected nodes in the tree.  Otherwise, use `NonIndexedChildren()` instead.
