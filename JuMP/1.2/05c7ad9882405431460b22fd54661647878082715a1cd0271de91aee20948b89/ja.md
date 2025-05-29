```
dual_status(model::Model; result::Int = 1)
```

最近の双対解のステータスを説明する [`MOI.ResultStatusCode`](@ref) を返します（すなわち、結果インデックス `result` に関連付けられた [`MOI.DualStatus`](@ref) 属性）。

関連情報: [`result_count`](@ref).
