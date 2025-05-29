```
start_value_function(vref::Union{InfiniteVariableRef, DerivativeRef})::Union{Nothing, Function}
```

Return the function that is used to generate the start values of `vref` for particular support values. Returns `nothing` if no start behavior has been specified.

**Example**

```julia-repl
julia> start_value_function(vref)
my_start_func
```
