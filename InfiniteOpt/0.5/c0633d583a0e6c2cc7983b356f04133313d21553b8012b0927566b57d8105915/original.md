```
JuMP.set_integer(vref::UserDecisionVariableRef)::Nothing
```

Extend `JuMP.set_integer` to specify an `InfiniteOpt` variable as a integer  variable. Errors if `vref` is an binary variable.

**Example**

```julia-repl
julia> set_integer(vref)

julia> is_integer(vref)
true
```
