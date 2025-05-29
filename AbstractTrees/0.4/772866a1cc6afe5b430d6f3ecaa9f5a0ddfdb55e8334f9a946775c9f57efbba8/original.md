```
childindices(tree, node_index)
```

Get the indices of the children of the node of tree `tree` specified by `node_index`.

To be consistent with [`children`](@ref), by default this returns an empty tuple.

**REQUIRED** for indexed trees:  Indexed trees, i.e. trees that do not implement [`children`](@ref) must implement this function.
