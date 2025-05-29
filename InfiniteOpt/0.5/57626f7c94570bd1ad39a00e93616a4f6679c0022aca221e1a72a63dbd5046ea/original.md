```
JuMP.set_objective_function(model::InfiniteModel,
                            func::JuMP.AbstractJuMPScalar)::Nothing
```

Extend `JuMP.set_objective_function` to set the objective expression of infinite model `model`. Errors if `func` contains infinite variables and/or parameters. Also errors if `func` contains invalid variables.

**Example**

```julia-repl
julia> set_objective_function(model, 2x + 1)

julia> objective_function(model)
2 x + 1
```
