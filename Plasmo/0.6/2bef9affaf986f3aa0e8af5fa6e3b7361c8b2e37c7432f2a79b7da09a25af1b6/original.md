```
JuMP.constraint_ref_with_index(backend::GraphMOIBackend, idx::MOI.Index)
```

Return the constraint reference (or variable reference) associated with the graph index  in `backend`. Returns a `JuMP.ConstraintRef` (or `NodeVariableRef`) object.
