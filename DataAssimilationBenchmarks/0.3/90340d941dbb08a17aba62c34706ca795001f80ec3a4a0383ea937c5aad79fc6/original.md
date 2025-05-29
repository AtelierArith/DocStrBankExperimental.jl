```
ParamSample = Dict{String, Vector{UnitRange{Int64}}}
```

Dictionary containing key and index pairs to subset the state vector and then merge a statistical sample of parameters that govern the equations of motion with the ParamDict `dx_params` in parameter estimation problems.
