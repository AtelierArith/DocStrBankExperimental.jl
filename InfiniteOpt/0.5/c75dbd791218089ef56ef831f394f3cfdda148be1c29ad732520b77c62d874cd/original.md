```
JuMP.FixRef(vref::SemiInfiniteVariableRef)::InfOptConstraintRef
```

Extend `JuMP.FixRef` to return the constraint reference of the fix constraint associated with the original infinite variable of `vref`. Errors `vref` is not fixed.

**Examples**

```julia-repl
julia> cref = FixRef(vref)
var == 1.0
```
