```
prevsibling(node)
```

Get the previous sibling (child of the same parent) of the tree node `node`.  The returned node should be the same as the node that would be returned prior to `node` when iterating over `(children ∘ parent)(node)`.

**OPTIONAL**: This function is optional in all cases.  Default AbstractTrees method assume that it is impossible to obtain the previous sibling and all iterators act in the "forward" direction.
