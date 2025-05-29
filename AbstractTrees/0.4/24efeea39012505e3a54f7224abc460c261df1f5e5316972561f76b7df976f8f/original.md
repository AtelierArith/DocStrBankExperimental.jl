```
StoredParents <: ParentLinks
```

Indicates that this node stores parent links explicitly. The implementation is responsible for defining the parentind function to expose this information.

If a node in a tree has this trait, so must all connected nodes.  If this is not the case, use [`ImplicitParents`](@ref) instead.

## Required Methods

  * [`parent`](@ref)
