```
JuMP.BinaryRef(vref::SemiInfiniteVariableRef)::InfOptConstraintRef
```

`JuMP.BinaryRef`を拡張して、`vref`の元の無限変数をバイナリに制約する制約への参照を返します。存在しない場合はエラーを返します。

**例**

```julia-repl
julia> cref = BinaryRef(vref)
var binary
```
