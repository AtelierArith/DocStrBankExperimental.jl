```
JuMP.build_variable(_error::Function, info::JuMP.VariableInfo, 
                    var_type::Infinite)::InfiniteVariable{GeneralVariableRef}
```

Build and return an infinite variable based on `info` and `var_type`. Errors if  the infinite parameter references included in `var_type` are invalid. See  [`Infinite`](@ref) for more information.

**Example**

```julia-repl
julia> info = VariableInfo(false, 0, false, 0, false, 0, true, 0, false, false);

julia> inf_var = build_variable(error, info, Infinite(t));
```
