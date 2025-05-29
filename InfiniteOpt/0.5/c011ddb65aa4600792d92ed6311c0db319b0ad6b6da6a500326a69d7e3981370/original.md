```
JuMP.objective_function_type(model::InfiniteModel)::Type{<:JuMP.AbstractJuMPScalar}
```

Extend `JuMP.objective_function_type` to return the objective function type of  infinite model `model`.

**Example**

```julia-repl
julia> objective_function_type(model)
GenericAffExpr{Float64,GeneralVariableRef}
```
