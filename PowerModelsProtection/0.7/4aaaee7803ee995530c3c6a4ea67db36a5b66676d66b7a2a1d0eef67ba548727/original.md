```
solve_fault_study(case::Dict{String,Any}, solver; kwargs...)
```

Solves a fault study using all active faults under `case["fault"]` for transmission (matpower) data sets given an optimization `solver`

`kwargs` can be any valid keyword argument for PowerModels' run_model function.
