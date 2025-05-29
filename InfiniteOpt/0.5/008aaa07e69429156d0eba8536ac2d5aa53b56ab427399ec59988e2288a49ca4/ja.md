```
infinite_variable_ref(vref::SemiInfiniteVariableRef)::GeneralVariableRef
```

半無限変数 `vref` に関連付けられた無限変数/導関数/パラメータ関数の参照を返します。

**例**

```julia-repl
julia> infinite_variable_ref(vref)
g(t, x)
```
