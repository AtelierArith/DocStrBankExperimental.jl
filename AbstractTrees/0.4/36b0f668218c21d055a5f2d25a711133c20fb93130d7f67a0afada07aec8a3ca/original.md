```
parentindex(tree, node_index)
```

Get the index of the parent of the node of tree `tree` specified by `node_index`.

Nodes that have no parent (i.e. the root node) should return `nothing`.

**OPTIONAL**: Indexed trees with the [`StoredParents`](@ref) trait must implement this.
