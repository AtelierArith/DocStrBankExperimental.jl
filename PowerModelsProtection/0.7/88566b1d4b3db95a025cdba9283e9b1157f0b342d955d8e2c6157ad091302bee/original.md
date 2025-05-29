```
solve_mc_fault_study(case::Dict{String,<:Any}, solver; kwargs...)
```

Function to solve a multiconductor (distribution) fault study given a data set `case` and optimization `solver`

`kwargs` can be any valid keyword argument for PowerModelsDistribution's `solve_mc_model`
