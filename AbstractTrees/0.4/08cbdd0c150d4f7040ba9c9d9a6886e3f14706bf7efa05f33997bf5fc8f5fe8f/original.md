```
ParentLinks(::Type{T})
ParentLinks(tree)
```

A trait which indicates whether a tree node stores references to its parents (`StoredParents()`) or if the parents must be inferred from the tree structure (`ImplicitParents()`).

Trees for which `ParentLinks` returns `StoredParents()` *MUST* implement [`parent`](@ref).

If `StoredParents()`, all nodes in the tree must also have `StoredParents()`, otherwise use `ImplicitParents()`.

**OPTIONAL**: This should be implemented for a tree if parents of nodes are stored

```julia
AbstractTrees.ParentLinks(::Type{<:TreeType}) = AbstractTrees.StoredParents()
parent(t::TreeType) = get_parent(t)
```
