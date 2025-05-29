```
JuMP.FixRef(vref::SemiInfiniteVariableRef)::InfOptConstraintRef
```

`JuMP.FixRef`を拡張して、`vref`の元の無限変数に関連付けられた固定制約の制約参照を返すようにします。エラー `vref` は固定されていません。

**例**

```julia-repl
julia> cref = FixRef(vref)
var == 1.0
```
