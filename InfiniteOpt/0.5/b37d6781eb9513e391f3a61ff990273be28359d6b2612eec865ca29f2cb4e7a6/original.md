```
JuMP.add_variable(model::InfiniteModel, var::PointVariable,
                  [name::String = ""])::GeneralVariableRef
```

Extend the `JuMP.add_variable` function to accomodate `PointVariable` variable  types. Adds a variable to an infinite model `model` and returns a  [`GeneralVariableRef`](@ref). Primarily intended to be an internal function of  the constructor macro `@variable`. However, it can be used in combination with `JuMP.build_variable` to add variables to an infinite model object. Errors if an invalid infinite variable reference is included in `var`.

**Example**

```julia-repl
julia> @infinite_parameter(m, t in [0, 10]);

julia> info = VariableInfo(false, 0, false, 0, false, 0, true, 0, false, false);

julia> inf_var = build_variable(error, info, Infinite(t));

julia> ivref = add_variable(m, inf_var, "var_name")
var_name(t)

julia> pt_var = build_variable(error, info, Point(ivref, 0.5));

julia> pvref = add_variable(m, pt_var, "var_alias")
var_alias
```
