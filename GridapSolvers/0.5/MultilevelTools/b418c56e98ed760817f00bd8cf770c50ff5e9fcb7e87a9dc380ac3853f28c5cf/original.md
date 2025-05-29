```
const FESpaceHierarchy = HierarchicalArray{<:FESpaceHierarchyLevel}
```

A `FESpaceHierarchy` is a hierarchical array of `FESpaceHierarchyLevel` objects. It stores the    adapted/redistributed fe spaces and the corresponding subcommunicators.

For convenience, implements some of the API of `FESpace`.
