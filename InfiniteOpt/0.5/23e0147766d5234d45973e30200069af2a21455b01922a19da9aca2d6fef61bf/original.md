```
JuMP.start_value(vref::UserDecisionVariableRef)::Union{Nothing, Float64}
```

Extend `JuMP.start_value` to return starting value of `InfiniteOpt` variable if  it has one. Returns `nothing` otherwise.

**Example**

```julia-repl
julia> start_value(vref)
0.0
```
