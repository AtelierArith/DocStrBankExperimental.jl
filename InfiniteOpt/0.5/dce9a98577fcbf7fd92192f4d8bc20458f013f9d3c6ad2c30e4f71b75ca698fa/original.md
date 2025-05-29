```
JuMP.list_of_constraint_types(model::InfiniteModel)::Vector{Tuple{DataType, DataType}}
```

Extend `JuMP.list_of_constraint_types` to return a list of tuples that contain  all the used combinations of function types and set types in the model.

**Example**

```julia-repl
julia> all_constraints(model)
3-element Array{Tuple{DataType,DataType},1}:
 (GeneralVariableRef, MathOptInterface.LessThan{Float64})
 (GeneralVariableRef, MathOptInterface.GreaterThan{Float64})
 (GeneralVariableRef, MathOptInterface.Integer)
```
