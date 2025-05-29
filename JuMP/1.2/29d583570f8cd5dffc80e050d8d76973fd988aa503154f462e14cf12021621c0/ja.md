```
start_value(con_ref::ConstraintRef)
```

制約 `con_ref` の原始開始値 ([`MOI.ConstraintPrimalStart`](@ref)) を返します。

注意: 原始開始値が設定されていない場合、`start_value` は `nothing` を返します。

関連情報: [`set_start_value`](@ref).
