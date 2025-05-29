```
JuMP.add_variable(model::InfiniteModel, var::InfiniteVariable,
                  [name::String = ""])::GeneralVariableRef
```

Extend the `JuMP.add_variable` function to accomodate infinite variable  types. Adds a variable to an infinite model `model` and returns a  [`GeneralVariableRef`](@ref). Primarily intended to be an internal function of  the constructor macro `@variable`. However, it can be used in combination with `JuMP.build_variable` to add  infinite variables to an infinite model object. Errors if invalid parameter reference(s) are included in `var`.

**Example**

```julia-repl
julia> @infinite_parameter(m, t in [0, 10]);

julia> info = VariableInfo(false, 0, false, 0, false, 0, true, 0, false, false);

julia> inf_var = build_variable(error, info, Infinite(t));

julia> ivref = add_variable(m, inf_var, "var_name")
var_name(t)
```
