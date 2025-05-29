```
JuMP.LowerBoundRef(vref::SemiInfiniteVariableRef)::InfOptConstraintRef
```

`JuMP.LowerBoundRef`を拡張して、`vref`の元の無限変数の下限の制約参照を抽出します。

**例**

```julia-repl
julia> cref = LowerBoundRef(vref)
var >= 0.0
```
