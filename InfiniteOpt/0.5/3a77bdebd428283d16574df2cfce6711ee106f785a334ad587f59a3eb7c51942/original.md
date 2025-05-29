```
JuMP.solver_name(model::InfiniteModel)
```

Extend `solver_name` to return the name of the solver being used if there is an  optimizer selected and it has a name attribute. Otherwise, an error is thrown.

**Example**

```julia-repl
julia> solver_name(model)
"Gurobi"
```
