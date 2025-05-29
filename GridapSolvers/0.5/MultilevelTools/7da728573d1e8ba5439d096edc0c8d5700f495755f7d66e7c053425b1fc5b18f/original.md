```
const ModelHierarchy = HierarchicalArray{<:ModelHierarchyLevel}
```

A `ModelHierarchy` is a hierarchical array of `ModelHierarchyLevel` objects. It stores the    adapted/redistributed models and the corresponding subcommunicators.

For convenience, implements some of the API of `DiscreteModel`.
