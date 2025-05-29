```
parameter_refs(vref::SemiInfiniteVariableRef)::Tuple
```

半無限変数 `vref` に関連付けられた無限パラメータ参照を返します。これは、評価されたパラメータが除外されることを除いて、未転写の無限変数を定義するために入力されたパラメータ参照を含む `Tuple` としてフォーマットされています。

**例**

```julia-repl
julia> parameter_refs(vref)
(t, [x[1], x[2]])
```
