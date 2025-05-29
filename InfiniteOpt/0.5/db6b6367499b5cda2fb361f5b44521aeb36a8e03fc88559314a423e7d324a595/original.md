```
JuMP.IntegerRef(vref::SemiInfiniteVariableRef)::InfOptConstraintRef
```

Extend `JuMP.IntegerRef` to return a constraint reference to the constraint constrainting the original infinite variable of `vref` to be integer. Errors if one does not exist.

**Example**

```julia-repl
julia> cref = IntegerRef(vref)
var integer
```
