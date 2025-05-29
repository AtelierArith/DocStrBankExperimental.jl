```
SiblingLinks(::Type{T})
SiblingLinks(tree)
```

A trait which indicates whether a tree node stores references to its siblings (`StoredSiblings()`) or must be inferred from the tree structure (`ImplicitSiblings()`).

If a node has the trait `StoredSiblings()`, so must all connected nodes in the tree.  Otherwise, use `ImplicitSiblings()` instead.

**OPTIONAL**: This should be implemented for a tree if siblings of nodes are stored

```julia
AbstractTrees.SiblingLinks(::Type{<:TreeType}) = AbstractTrees.StoredSiblings()
```
