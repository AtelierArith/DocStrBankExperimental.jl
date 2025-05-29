```
connectednodes(fes::AbstractFESet)
```

Extract the node numbers of the nodes connected by given finite elements.

Extract the list of unique node numbers for the nodes that are connected by the finite element set `fes`. Note that it is assumed that all the FEs are of the same type (the same number of connected nodes by each cell).
