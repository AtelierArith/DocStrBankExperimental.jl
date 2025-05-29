```
JuMP.num_constraints(model::InfiniteModel, [function_type], [set_type])::Int
```

Extend `JuMP.num_constraints` to return the number of constraints with a  partiuclar function type and set type.

**Example**

```julia-repl
julia> num_constraints(model, FiniteVariableRef, MOI.LessThan)
1

julia> num_constraints(model, FiniteVariableRef)
3

julia> num_constraints(model, MOI.LessThan)
2

julia> num_constraints(model)
4
```
