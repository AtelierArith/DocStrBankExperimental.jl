```
multiphase_bus_variable_container(; default::DefaultType=missing)
```

Return a DefaultDict of DefaultDict with three key types for indexing variables on:

1. `AbstractString` for bus names
2. `Int` for time step
3. `AbstractVecOrMat` for vectors or matrices of phase variables
