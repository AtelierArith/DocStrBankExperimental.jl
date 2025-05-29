```
graph_index(
    backend::GraphMOIBackend, 
    ref::RT
) where {RT<:Union{NodeVariableRef,ConstraintRef}}
```

Return the actual variable or constraint index of the backend model that corresponds to the local index of a node or edge.
