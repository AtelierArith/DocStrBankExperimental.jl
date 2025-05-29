```
JuMP.BinaryRef(vref::UserDecisionVariableRef)::InfOptConstraintRef
```

`JuMP.BinaryRef`を拡張して、`vref`をバイナリに制約する制約の参照を返します。存在しない場合はエラーを返します。

**例**

```julia-repl
julia> cref = BinaryRef(vref)
var binary
```
