```
all_elasticities(problem::FRACProblem, 
    results::Dict{Any,Any}; 
    I = 50, 
    product = 1, 
    by_value = nothing)
```

This function takes a `FRACProblem` and a dictionary of results as arguments. The dictionary of results should be the output of the `estimate!` function. It is an internal function that is not intended to be called by the user directly.
