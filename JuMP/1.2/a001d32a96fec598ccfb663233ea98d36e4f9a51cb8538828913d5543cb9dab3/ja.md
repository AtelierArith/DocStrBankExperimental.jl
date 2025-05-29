```
set_start_value(con_ref::ConstraintRef, value)
```

制約 `con_ref` のプライマル開始値 ([`MOI.ConstraintPrimalStart`](@ref)) を `value` に設定します。プライマル開始値を削除するには、`nothing` に設定します。

関連情報として [`start_value`](@ref) も参照してください。
