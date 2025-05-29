```
JuMP.UpperBoundRef(vref::UserDecisionVariableRef)::InfOptConstraintRef
```

`JuMP.UpperBoundRef`を拡張して、`vref`の上限の制約参照を抽出します。

**例**

```julia-repl
julia> cref = UpperBoundRef(vref)
var ≤ 1.0
```
