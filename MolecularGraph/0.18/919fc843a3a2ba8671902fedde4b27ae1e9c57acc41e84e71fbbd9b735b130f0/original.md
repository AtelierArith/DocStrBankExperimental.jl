```
maximum_common_subgraph(g::ConstraintArrayMCES, h::ConstraintArrayMCES;
    connected=false, kwargs...) -> (Dict, Symbol)
```

Compute maximum common edge-induced subgraph (MCES) between the two MCS constraints.
