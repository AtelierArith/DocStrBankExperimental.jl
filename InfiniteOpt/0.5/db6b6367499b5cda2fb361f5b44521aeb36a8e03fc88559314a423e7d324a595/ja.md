```
JuMP.IntegerRef(vref::SemiInfiniteVariableRef)::InfOptConstraintRef
```

`JuMP.IntegerRef`を拡張して、`vref`の元の無限変数を整数に制約する制約への参照を返します。存在しない場合はエラーを返します。

**例**

```julia-repl
julia> cref = IntegerRef(vref)
var integer
```
