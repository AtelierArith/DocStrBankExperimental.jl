```
JuMP.add_variable(model::InfiniteModel, var::JuMP.ScalarVariable,
                  [name::String = ""])::GeneralVariableRef
```

Extend the `JuMP.add_variable` function to accomodate finite (scalar) variable  types. Adds a variable to an infinite model `model` and returns a  [`GeneralVariableRef`](@ref). Primarily intended to be an internal function of  the constructor macro `@variable`. However, it can be used in combination with `JuMP.build_variable` to add finite variables to an infinite model object.

**Examples**

```julia-repl
julia> f_var = build_variable(error, info);

julia> fvref = add_variable(m, f_var, "var_name")
var_name
```
