```
JuMP.build_variable(_error::Function, info::JuMP.VariableInfo, 
                    var_type::Point)::InfiniteVariable{GeneralVariableRef}
```

Build and return a point variable based on `info` and `var_type`. Errors  if the information stored in `var_type` is invalid. See [`Point`](@ref)  for more information.

**Example**

```julia-repl
julia> y
y(t)

julia> info = VariableInfo(false, 0, false, 0, false, 0, true, 0, false, false);

julia> pt_var = build_variable(error, info, SemiInfinite(y, 0));
```
