```
JuMP.IntegerRef(vref::UserDecisionVariableRef)::InfOptConstraintRef
```

`JuMP.IntegerRef`を拡張して、`vref`を整数に制約する制約の参照を返します。存在しない場合はエラーを返します。

**例**

```julia-repl
julia> cref = IntegerRef(vref)
var integer
```
