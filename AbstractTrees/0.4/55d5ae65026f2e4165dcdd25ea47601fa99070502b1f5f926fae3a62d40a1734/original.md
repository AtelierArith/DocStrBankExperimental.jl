```
nextsiblingindex(tree, node_index)
```

Get the index of the next sibling of the node of tree `tree` specified by `node_index`.

Nodes which have no next sibling should return `nothing`.

**OPTIONAL**: Indexed trees with the [`StoredSiblings`](@ref) trait must implement this.
