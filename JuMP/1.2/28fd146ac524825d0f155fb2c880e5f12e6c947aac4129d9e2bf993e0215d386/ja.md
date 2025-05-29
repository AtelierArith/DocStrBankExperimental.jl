```
dual_start_value(con_ref::ConstraintRef)
```

制約 `con_ref` の双対開始値 (MOI 属性 `ConstraintDualStart`) を返します。

注意: 双対開始値が設定されていない場合、`dual_start_value` は `nothing` を返します。

関連情報: [`set_dual_start_value`](@ref).
