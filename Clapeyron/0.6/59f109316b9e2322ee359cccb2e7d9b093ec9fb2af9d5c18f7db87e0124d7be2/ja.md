```
has_reference_state(model)::Bool
```

入力された `EoSModel` が参照状態を持っているかどうかをチェックします。`true/false` を返します。

## 例

```julia-repl
julia> has_reference_state(PCSAFT("water"))
false

julia> has_reference_state(PCSAFT("water",idealmodel = ReidIdeal))
true
```

デフォルトの idealmodel (`BasicIdeal`) は参照状態を設定することを許可していないことに注意してください。
