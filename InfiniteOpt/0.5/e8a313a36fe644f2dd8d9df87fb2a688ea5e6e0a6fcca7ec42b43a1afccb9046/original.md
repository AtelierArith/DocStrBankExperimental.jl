```
JuMP.objective_function(model::InfiniteModel)::JuMP.AbstractJuMPScalar
```

Extend `JuMP.objective_function` to return the objective of infinite model  `model`.

**Example**

```julia-repl
julia> objective_function(model)
1
```
