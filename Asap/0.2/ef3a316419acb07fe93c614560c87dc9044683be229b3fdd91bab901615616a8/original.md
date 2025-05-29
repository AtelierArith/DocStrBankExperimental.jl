```
solve!(model::TrussModel; reprocess = false)
```

Solve for the nodal displacements of a structural truss model. `reprocess = true` reevaluates all node/element properties and reassembles the global stiffness matrix.
