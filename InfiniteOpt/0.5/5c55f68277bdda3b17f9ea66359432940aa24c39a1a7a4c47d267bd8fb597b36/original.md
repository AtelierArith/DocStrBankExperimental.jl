```
JuMP.UpperBoundRef(vref::UserDecisionVariableRef)::InfOptConstraintRef
```

Extend `JuMP.UpperBoundRef` to extract a constraint reference for the upper  bound of `vref`.

**Example**

```julia-repl
julia> cref = UpperBoundRef(vref)
var ≤ 1.0
```
