```
multiphase_edge_variable_container(; default::DefaultType=missing)
```

Return a DefaultDict of DefaultDict with three key types for indexing variables on:

1. `Tuple{String, String}` for edge names
2. `Int` for time step
3. `AbstractVecOrMat` for vectors or matrices of phase variables
