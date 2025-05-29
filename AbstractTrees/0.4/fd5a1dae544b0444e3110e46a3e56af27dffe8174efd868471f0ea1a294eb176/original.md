```
prevsiblingindex(tree, node_index)
```

Get the index of the previous sibling of the node of tree `tree` specified by `node_index`.

Nodes which have no previous sibling should return `nothing`.

**OPTIONAL**: Indexed trees that have [`StoredSiblings`](@ref) can implement this, but no built-in tree algorithms require it.
