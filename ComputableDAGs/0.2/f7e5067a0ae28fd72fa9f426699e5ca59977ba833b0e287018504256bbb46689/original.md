```
Edge
```

Type of an edge in the graph. Edges can only exist between a [`DataTaskNode`](@ref) and a [`ComputeTaskNode`](@ref) or vice versa, not between two of the same type of node.

An edge always points from child to parent: `child = e.edge[1]` and `parent = e.edge[2]`. Additionally, the `Edge``contains the`index` which is used as the child's index in the parent node.

The child is the prerequisite node of the parent.
