```
JuMP.set_binary(vref::UserDecisionVariableRef)::Nothing
```

Extend `JuMP.set_binary` to specify an `InfiniteOpt` variable as a binary  variable. Errors if `vref` is an integer variable.

**Example**

```julia-repl
julia> set_binary(vref)

julia> is_binary(vref)
true
```
