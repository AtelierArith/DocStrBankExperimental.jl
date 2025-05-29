```
solve!(model::Model; reprocess = false)
```

Solve for the nodal displacements of a structural model. `reprocess = true` reevaluates all node/element properties and reassembles the global stiffness matrix.
