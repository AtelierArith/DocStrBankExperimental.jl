```
set_start_value_function(vref::InfiniteVariableRef,
                         start::Union{Real, Function})::Nothing
```

Set the start value function of `vref`. If `start::Real` then a function is generated to such that the start value will be `start` for the entire infinite domain. If `start::Function` then this function should map to a scalar start value given a support value arguments matching the format of the parameter elements in `parameter_refs(vref)`.

**Example**

```julia-repl
julia> set_start_value_function(vref, 1) # all start values will be 1

julia> set_start_value_function(vref, my_func) # each value will be made via my_func
```
