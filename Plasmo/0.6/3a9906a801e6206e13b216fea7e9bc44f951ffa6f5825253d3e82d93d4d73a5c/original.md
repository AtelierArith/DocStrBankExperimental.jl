```
JuMP.relax_integrality(graph::OptiGraph)
```

Relax all binary and integer constraints in `graph`. Return a function that un-relaxes the graph by re-adding the binary and/or integer constraints.
