```
reduced_cost(x::VariableRef)::Float64
```

変数 `x` に関連する削減コストを返します。

アクティブな変数の制約のシャドウプライスを照会することに相当します（存在し、アクティブである場合）。

参照: [`shadow_price`](@ref)。
