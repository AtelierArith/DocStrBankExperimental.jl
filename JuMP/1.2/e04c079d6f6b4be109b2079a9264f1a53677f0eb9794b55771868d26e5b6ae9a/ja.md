```
dual_objective_value(model::Model; result::Int = 1)
```

最も最近ソルバーによって返された解の結果インデックス `result` に関連付けられた双対問題の目的値を返します。

ソルバーがこの属性をサポートしていない場合、`MOI.UnsupportedAttribute{MOI.DualObjectiveValue}` をスローします。

関連情報: [`result_count`](@ref).
