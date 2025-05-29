```
JuMP.LowerBoundRef(vref::SemiInfiniteVariableRef)::InfOptConstraintRef
```

Extend `JuMP.LowerBoundRef` to extract a constraint reference for the lower bound of the original infinite variable of `vref`.

**Example**

```julia-repl
julia> cref = LowerBoundRef(vref)
var >= 0.0
```
