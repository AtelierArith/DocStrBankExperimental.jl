```
JuMP.list_of_constraint_types(model::AbstractSpGpModel) -> Vector{Tuple{DataType,DataType}}
```

Returns a list of constraint types in the model as (function*type, set*type) tuples.

# Returns

  * A vector of tuples where each tuple contains the function type and set type of a constraint
