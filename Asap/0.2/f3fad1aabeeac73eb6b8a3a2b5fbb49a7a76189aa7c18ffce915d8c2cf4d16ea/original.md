```
process!(model::TrussModel)
```

Process a structural truss model: add linkages between nodes and elements, determine DOF orders, generate the load vector P, and assemble the global stiffness matrix, S.
