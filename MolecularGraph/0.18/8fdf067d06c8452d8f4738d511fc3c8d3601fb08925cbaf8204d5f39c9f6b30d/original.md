```
maximum_common_subgraph(g::ConstraintArrayMCIS, h::ConstraintArrayMCIS;
    connected=false, kwargs...) -> (Dict, Symbol)
```

Compute maximum common node-induced subgraph (MCIS) between the two MCS constraints.
