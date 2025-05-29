```
children(node)
```

Get the immediate children of node `node`.

By default, every object is a parent node of an empty set of children.  This is to make it simpler to define trees with nodes of different types, for example arrays are trees regardless of their `eltype`.

**REQUIRED**: This is required for all tree nodes with non-empty sets of children.  If it is not possible to infer the children from the node alone, this should be defined for a wrapper object which does.
