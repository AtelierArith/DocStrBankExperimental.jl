```
JuMP.LowerBoundRef(vref::UserDecisionVariableRef)::InfOptConstraintRef
```

Extend `JuMP.LowerBoundRef` to extract a constraint reference for the lower  bound of `vref`.

**Example**

```julia-repl
var ≥ 0.0
```
