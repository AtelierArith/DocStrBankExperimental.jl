```
JuMP.index(vref::GeneralVariableRef)::AbstractInfOptIndex
```

Extend `JuMP.index` to return the appropriate index of `vref`.

**Example**

```julia-repl
julia> index(vref)
FiniteVariableIndex(1)
```
