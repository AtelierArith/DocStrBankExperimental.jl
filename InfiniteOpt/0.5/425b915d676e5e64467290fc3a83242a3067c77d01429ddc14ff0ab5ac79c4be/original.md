```
reset_start_value_function(vref::InfiniteVariableRef)::Nothing
```

Remove the existing start value function and return to the default. Generally, this is triggered by deleting an infinite parameter that `vref` depends on.

**Example**

```julia-repl
julia> reset_start_value_function(vref)
```
