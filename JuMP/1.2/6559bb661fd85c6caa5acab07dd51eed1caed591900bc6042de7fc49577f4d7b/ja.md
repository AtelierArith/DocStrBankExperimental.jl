```
set_dual_start_value(con_ref::ConstraintRef, value)
```

制約 `con_ref` の双対開始値 (MOI 属性 `ConstraintDualStart`) を `value` に設定します。双対開始値を削除するには、`nothing` に設定します。

関連情報は [`dual_start_value`](@ref) を参照してください。
