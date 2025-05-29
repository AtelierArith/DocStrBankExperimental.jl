```
JuMP.FixRef(vref::UserDecisionVariableRef)::InfOptConstraintRef
```

Extend `JuMP.FixRef` to return the constraint reference of the fix constraint  associated with `vref`. Errors `vref` is not fixed.

**Examples**

```julia-repl
julia> cref = FixRef(vref)
var = 1.0
```
