```
nextsibling(node)
```

Get the next sibling (child of the same parent) of the tree node `node`.  The returned node should be the same as the node that would be returned after `node` when iterating over `(children ∘ parent)(node)`.

**OPTIONAL**: This function is required for nodes with the [`StoredSiblings`](@ref) trait.  There is no default definition.
