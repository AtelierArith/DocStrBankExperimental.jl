```
JuMP.FixRef(vref::UserDecisionVariableRef)::InfOptConstraintRef
```

`JuMP.FixRef`を拡張して、`vref`に関連付けられた固定制約の制約参照を返すようにします。エラー `vref` は固定されていません。

**例**

```julia-repl
julia> cref = FixRef(vref)
var = 1.0
```
