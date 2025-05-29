```
get_model(vardata::VariableData, timeout::Float64=Inf, all_solutions::Bool=false)::Tuple{Model,OrderedDict}
```

Return a JuMP model created using `vardata`, and an OrderedDict of the variables defined in the model.

# Arguments

  * `vardata::VariableData`: VariableData object representing the variables and constraints to be added to the model.
  * `timeout::Float64=Inf`: Float representing the maximum time to run the model.
  * `all_solutions::Bool=false`: Bool representing whether to return all solutions or just the first.

# Notes

  * Create a model with the correct variables, and adds constraints to the model.
  * The variables defined are anonymous, so they are stored in an OrderedDict mapped to their int representation.
