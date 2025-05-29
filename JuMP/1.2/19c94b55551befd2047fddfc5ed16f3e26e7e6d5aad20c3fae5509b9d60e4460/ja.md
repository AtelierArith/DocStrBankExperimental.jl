```
start_value(v::VariableRef)
```

変数 `v` の開始値 (MOI 属性 `VariablePrimalStart`) を返します。

注意: `VariablePrimalStart` は時々「MIP-starts」または「warmstarts」と呼ばれます。

関連情報は [`set_start_value`](@ref) を参照してください。
