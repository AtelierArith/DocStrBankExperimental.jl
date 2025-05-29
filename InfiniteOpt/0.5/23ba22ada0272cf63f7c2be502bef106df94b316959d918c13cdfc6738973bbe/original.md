```
JuMP.variable_by_name(model::InfiniteModel,
                      name::String)::Union{GeneralVariableRef, Nothing}
```

Extend `JuMP.variable_by_name` for `InfiniteModel` objects. Return the variable  reference assoociated with a variable name. Errors if multiple variables have the  same name. Returns nothing if no such name exists.

**Examples**

```julia-repl
julia> variable_by_name(m, "var_name")
var_name

julia> variable_by_name(m, "fake_name")

```
