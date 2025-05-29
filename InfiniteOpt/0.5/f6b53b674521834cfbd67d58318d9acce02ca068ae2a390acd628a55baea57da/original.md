```
JuMP.BinaryRef(vref::UserDecisionVariableRef)::InfOptConstraintRef
```

Extend `JuMP.BinaryRef` to return a constraint reference to the constraint  constrainting `vref` to be binary. Errors if one does not exist.

**Example**

```julia-repl
julia> cref = BinaryRef(vref)
var binary
```
