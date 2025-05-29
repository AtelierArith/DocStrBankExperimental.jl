```
JuMP.UpperBoundRef(vref::SemiInfiniteVariableRef)::InfOptConstraintRef
```

`JuMP.UpperBoundRef`を拡張して、`vref`の元の無限変数の上限の制約参照を抽出します。

**例**

```julia-repl
julia> cref = UpperBoundRef(vref)
var <= 1.0
```
