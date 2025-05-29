```
set_start_value(variable::VariableRef, value::Union{Real,Nothing})
```

`variable`の開始値（MOI属性`VariablePrimalStart`）を`value`に設定します。

開始値を解除するには`nothing`を渡します。

注意: `VariablePrimalStart`は時々「MIP-start」または「ウォームスタート」と呼ばれます。

[`start_value`](@ref)も参照してください。
