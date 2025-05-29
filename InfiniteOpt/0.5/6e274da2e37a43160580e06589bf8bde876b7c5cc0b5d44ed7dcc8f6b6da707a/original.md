```
JuMP.build_variable(_error::Function, info::JuMP.VariableInfo, 
                    var_type::SemiInfinite)::SemiInfiniteVariable{GeneralVariableRef}
```

Build and return a semi-infinite variable based on `info` and `var_type`. Errors  if the information stored in `var_type` is invalid. See [`SemiInfinite`](@ref)  for more information.

**Example**

```julia-repl
julia> y
y(t, x)

julia> info = VariableInfo(false, 0, false, 0, false, 0, true, 0, false, false);

julia> semi_inf_var = build_variable(error, info, SemiInfinite(y, t, 0));
```
