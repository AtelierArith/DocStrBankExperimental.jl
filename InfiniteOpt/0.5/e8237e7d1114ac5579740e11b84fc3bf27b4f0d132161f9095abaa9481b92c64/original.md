```
JuMP.BinaryRef(vref::SemiInfiniteVariableRef)::InfOptConstraintRef
```

Extend `JuMP.BinaryRef` to return a constraint reference to the constraint constrainting the original infinite variable of `vref` to be binary. Errors if one does not exist.

**Example**

```julia-repl
julia> cref = BinaryRef(vref)
var binary
```
