```
JuMP.IntegerRef(vref::UserDecisionVariableRef)::InfOptConstraintRef
```

Extend `JuMP.IntegerRef` to return a constraint reference to the constraint  constrainting `vref` to be integer. Errors if one does not exist.

**Example**

```julia-repl
julia> cref = IntegerRef(vref)
var integer
```
