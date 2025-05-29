```
JuMP.build_variable(_error::Function, info::JuMP.VariableInfo, 
                    var_type::Deriv)::InfiniteVariable{GeneralVariableRef}
```

Build and return a first order derivative based on `info` and `var_type`. Errors  if the information in `var_type` is invalid. See [`Deriv`](@ref) for more  information.

**Example**

```julia-repl
julia> info = VariableInfo(false, 0, false, 0, false, 0, true, 0, false, false);

julia> deriv_var = build_variable(error, info, Deriv(y, t));
```
