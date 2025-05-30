```
JuMP.num_constraints(model::AbstractSpGpModel, function_type=nothing, set_type=nothing; 
                     count_variable_in_set_constraints::Bool = true) -> Int
```

Returns the number of constraints in the model.

# Arguments

  * `model::AbstractSpGpModel`: The geometric programming model
  * `function_type`: Optional type of constraint function to count
  * `set_type`: Optional type of constraint set to count
  * `count_variable_in_set_constraints::Bool`: Whether to count variable bounds as constraints

# Returns

  * The number of constraints matching the specified types, or all constraints if no types specified
