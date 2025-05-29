```
JuMP.constraint_by_name(model::InfiniteModel,
                        name::String)::Union{InfOptConstraintRef, Nothing}
```

Extend `JuMP.constraint_by_name` to return the constraint reference associated with `name` if one exists or returns nothing. Errors if more than one constraint uses the same name.

**Example**

```julia-repl
julia> constraint_by_name(model, "constr_name")
constr_name : x + pt = 3.0
```
